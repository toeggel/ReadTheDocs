# Tools

A list of tools, frameworks and more where I had good experience with or I got recommendation from others.

##  Documentation as Code (DoC)

- [PlantUML](https://plantuml.com/)
- [mermaid](https://mermaid-js.github.io/)
- [Structurizr](https://structurizr.com/)

## Infrastructure as Code (IaC)

- [terraform](https://www.terraform.io/)

## Mail Send

- [SendGrid](https://sendgrid.com/) - A cloud-based email delivery service designed for sending transactional and marketing emails at scale.
	- In combination with [FluentMail](https://github.com/lukencode/FluentEmail)
- [mailtrap](https://mailtrap.io/) - Primarily used by developers and QA professionals for testing email functionality in development and staging environments without sending emails to real users.
	- In combination with [FluentMail](https://github.com/lukencode/FluentEmail)
- [smtp4dev](https://github.com/rnwood/smtp4dev) - the fake SMTP email server for development and testing.

## Document Generation

- [Aspose.Words](https://products.aspose.com/words/net/)

## Contract Testing (over multiple APIs)

- [Pact](https://docs.pact.io/)
	- Contract testing can partially be achieved by Integration tests by using anonymous (or test) entities instead of instances of the real class => Test still green --> contract violation

## IdP

- [Duende Identity Server](https://duendesoftware.com/products/identityserver)
- (Azure B2C) rather bad experience (especially for heavy customization / personalization)

## Messaging

- [MassTransit](https://masstransit-project.com/)
	- Is able to handle Azure Event Hubs

## Feature toggling

- [Flagsmith](https://flagsmith.com/)

Others recommendations

- [LaunchDarkly](https://launchdarkly.com/)
- Default Microsoft FeatureManager

## Vulnerability monitoring

SAST (Static Application Security Testing)
DAST (Dynamic Application Security Testing)
IAST (Interactive Application Security Testing)
SCA (Software Composition Analysis)

* [mend.io](https://www.mend.io/) (formerly Whitesource) - Has established itself in the .NET world
* [SNYK](https://snyk.io/)

## Testing / Mocking

- [Respawn](https://github.com/jbogard/Respawn ) - To reset test data in integration tests (faster than DB deletion/re-creation or table truncation).
- Bogus vs. AutoFixtures
- Moq.AutoMocker
- [WireMock.Net](https://github.com/WireMock-Net/WireMock.Net)  - mimics the behaviour of an HTTP API

Never used or recommended so far but maybe useful:

* [NetArchTest](https://github.com/BenMorris/NetArchTest) -  allows you to create tests that enforce conventions for class design, naming and dependency in .Net code bases.
## Resilience 

- [Polly](https://github.com/App-vNext/Polly)
- Microsoft.Extensions.Http.Resilience 
	- https://www.youtube.com/watch?v=kNzssE7Ir60
	- See: https://learn.microsoft.com/en-us/dotnet/core/resilience/http-resilience?tabs=dotnet-cli 

## OpenAPI GUI

- Swagger ,but since it is no longer default starting with .NET9 we might also consider [Scalar](https://github.com/scalar/scalar)

## Benchmark
- [BenchmarkDotNet ](https://github.com/dotnet/BenchmarkDotNet )- No experience so far but looks easy to use