---
tags:
  - dotNet
---

# Validation

See: https://event-driven.io/en/explicit_validation_in_csharp_just_got_simpler/

## Example / end solution
	
```csharp
public static class Validation
{
	public static Guid AssertNotEmpty(
		[NotNull] this Guid? value,
		[CallerArgumentExpression("value")] string? argumentName = null
	) =>
		(value != null && value.Value != Guid.Empty)
			? value.Value
			: throw new ArgumentOutOfRangeException(argumentName);


	public static string AssertNotEmpty(
		[NotNull] this string? value,
		[CallerArgumentExpression("value")] string? argumentName = null
	) =>
		!string.IsNullOrWhiteSpace(value)
			? value
			: throw new ArgumentOutOfRangeException(argumentName);


	public static string? AssertNullOrNotEmpty(
		this string? value,
		[CallerArgumentExpression("value")] string? argumentName = null
	) =>
		value?.AssertNotEmpty(argumentName);

	public static string AssertMatchesRegex(
		[NotNull] this string? value,
		[StringSyntax(StringSyntaxAttribute.Regex)]
		string pattern,
		[CallerArgumentExpression("value")] string? argumentName = null
	) =>
		Regex.IsMatch(value.AssertNotEmpty(), pattern)
			? value
			: throw new ArgumentOutOfRangeException(argumentName);

	public static int AssertPositive(
		[NotNull] this int? value,
		[CallerArgumentExpression("value")] string? argumentName = null
	) =>
		value?.AssertPositive() ?? throw new ArgumentOutOfRangeException(argumentName);

	public static int AssertPositive(
		this int value,
		[CallerArgumentExpression("value")] string? argumentName = null
	) =>
		value > 0
			? value
			: throw new ArgumentOutOfRangeException(argumentName);
}
```

```csharp
public readonly record struct ProductId(Guid Value)
{
	public static ProductId From(Guid? productId) =>
		new(productId.AssertNotEmpty());
}

public readonly record struct SKU(string Value)
{
	public static SKU From(string? sku) =>
		new(sku.AssertMatchesRegex("[A-Z]{2,4}[0-9]{4,18}"));
}

public record RegisterProduct(
	ProductId ProductId,
	SKU SKU,
	string Name,
	string? Description
)
{
	public static RegisterProduct From(Guid? id, string? sku, string? name, string? description) =>
		new(
			ProductId.From(id),
			SKU.From(sku),
			name.AssertNotEmpty(),
			description.AssertNullOrNotEmpty()
		);
}
```

```csharp
endpoints.MapPost(
		"api/products/",
		async (
			ProductsDBContext dbContext,
			RegisterProductRequest request,
			CancellationToken ct
		) =>
		{
			var (sku, name, description) = request;
			var productId = Guid.NewGuid();

			var command = RegisterProduct.From(productId, sku, name, description);

			await Handle(
				dbContext.AddAndSave,
				dbContext.ProductWithSKUExists,
				command,
				ct
			);

			return Created($"/api/products/{productId}", productId);
		})
	.Produces(StatusCodes.Status201Created)
	.Produces(StatusCodes.Status400BadRequest);


// we're embracing here that we can expect anything from the UI
public record RegisterProductRequest(
	string SKU,
	string Name,
	string? Description
);
```
