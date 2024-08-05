---
tags:
  - dotNet
  - Database
  - best-practice
  - entity-framework
---

# Entity Framework

## Best Practices

 - Use `Select` to load less data from the DB
```csharp
// ❌ Bad Example -> Loads all user data from DB
var user = users.SingleOrDefault(u => u.Id == request.Id);
var dto = user.Select(u => new UserDto(u.FirstName));

// ✅ Good Example -> Loads only FirstName from DB
users.Select(u => new UserDto(u.FirstName))
	.SingleOrDefault(u => u.Id == request.Id);
```
 - Prevent a  *cartesian explosion* by using `SplitQuery` in cases where we have a lot of data getting joined. This reduces the data loaded but has some overhead and should therefore only be used when we expect to have a lot of DB in the table.
```csharp
// ❌ Bad Example -> Loads a blog multiple times (once for each post)
var blogs = context.Blogs
	.Include(blog => blog.Posts)
	.ToList();
	
// ✅ Good Example -> Loads The blog post only once
var blogs = context.Blogs
	.Include(blog => blog.Posts)
	.AsSplitQuery() // <== 👁️
	.ToList();
```
- ````
