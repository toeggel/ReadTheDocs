# [MyProject Name]

## Overview

[MyProject Short Description]

## Tech Stack

- .NET 9

## Project Structure

- **src/MyProject**: this project contains our application; any features should be added here
- **src/MyProject.Tests**: the tests are written with NUnit

## Architecture

We are using an approach called "vertical slices". This means we place all the code related to a specific functionality in a single directory. Only some top-level files are not in directories (i.e. `AssemblyAttributes.cs`, `GlobalUsings.cs`, and `Program.cs`). The test project follows the same structure.

Each vertical slice contains some documentation files with details about it:

- `ARCHITECTURE.md`: high-level overview of the contracts, components, used patterns, design decisions, failure modes / error handling, and testing approach
- `REQUIREMENTS.md`: the high-level description of the slice in terms of user-facing behavior

When you need to reference another slice, you can first look at these files to get the most important information, and only look at the implementation itself if the files do not contain sufficient information.

In addition to the vertical slices there are two special directories:

- `Core`: this directory contains shared infrastructure code which is not directly related to any particular functionality, for example the general `ProgramHost`
- `SharedKernel`: this contains all business logic which needs to be shared across multiple slices

Vertical slices are only allowed to reference code in their own slice, other slice's functionality through their contracts (and service collection extensions), as well as `Core` and `SharedKernel`. They MUST NOT reference implementation code in another vertical slice, only contracts. While implementing a feature, if you find code you would like to re-use across slices, you can extract it to the `SharedKernel`. But do so cautiously to not introduce unnecessary coupling.

The application consists of only a single main project which contains the WebApi.

### Existing Vertical Slices

The application currently contains the following vertical slices:

- **GetXyz**: Allows getting the xyz value 

- **PostXyz**: Updates the xyz with the specific value

### Used Libraries

Here is the list of libraries we use. Unless explicitly instructed, you must not add any additional dependencies. This means you MUST NOT update any csproj file or add any package via the dotnet CLI or otherwise unless explicitly instructed. However, please suggest possible new dependencies where it makes sense.
### NUnit 4

This is the [repository](https://github.com/nunit/nunit).

The documentation can be found [online](https://docs.nunit.org/articles/nunit/intro.html).

We use this library for all tests.

## Testing Infrastructure

Our testing approach uses comprehensive end-to-end testing.

### Test Architecture

#### Test Helpers (`src/[MyProject].Tests/`)

- **`TestHost.cs`**: Main test host that manages the application lifecycle
  - Provides `TestHost.Create()` factory method

- **`OtherClass.cs`**: Manages test timing and cancellation
  - `MyHelperMethod()` helps with stuff

#### Test Patterns

**Basic Test Structure:**

```csharp
[Test]
public async Task GivenCondition_WhenAction_ThenExpectedResult()
{
    using var timeouts = TestTimeouts.Create();
    var timeoutToken = timeouts.TestTimeoutToken;

    await using var host = TestHost.Create();

    // Setup initial state
    // ...

    // Run the application
    host.Run(timeoutToken, "increment", "foo", "5");

    // Perform action
    // ...

    // Assert results with polling
    await Assert.ThatAsync(
        async () => { /* condition check */ },
        Is.EqualTo(expectedValue)
            .After(timeouts.AssertionTimeoutInMs)
            .MilliSeconds.PollEvery(TestTimeouts.PollingIntervalInMs)
            .MilliSeconds
    );
}
```

**Key Testing Practices:**

- **End-to-End Testing**: All tests execute the full application as a user would
- **Async Assertions**: Use `Assert.ThatAsync` with polling for file system operations
- **Timeout Management**: Always use `TestTimeouts` for consistent timeout handling
- **Resource Cleanup**: Use `using` and `await using` for proper disposal
- **Isolated Test Data**: Each test creates unique directories to avoid interference

#### Assertion Patterns

We are using the NUnit fluent assertions.

**Simple Synchronous Assertion:**

```csharp
Assert.That(fileCount, Is.EqualTo(5));
```

**Simple Asynchronous Assertion:**

```csharp
await Assert.ThatAsync(() => fileCountTask, Is.EqualTo(5));
```

> IMPORTANT: We must only use async assertions when necessary. If the result we are asserting on is synchronous, we should also use a synchronous assertion.

**Eventual Synchronous Assertion:**

```csharp
Assert.That(
    () => fileCount, 
    Is.EqualTo(expectedContent)
        .After(timeouts.AssertionTimeoutInMs)
        .MilliSeconds.PollEvery(TestTimeouts.PollingIntervalInMs)
        .MilliSeconds
);
```

**Eventual Asynchronous Assertion:**

```csharp
await Assert.ThatAsync(
    () => fileCountTask, 
    Is.EqualTo(expectedContent)
        .After(timeouts.AssertionTimeoutInMs)
        .MilliSeconds.PollEvery(TestTimeouts.PollingIntervalInMs)
        .MilliSeconds
);
```

> IMPORTANT: We must only use async assertions when necessary. If the result we are asserting on is synchronous, we should also use a synchronous assertion.

**File Content Verification:**

```csharp
await Assert.ThatAsync(
    async () =>
    {
        var fileInfo = new FileInfo(filePath);
        if (fileInfo.Exists)
        {
            return await File.ReadAllTextAsync(filePath, cancellationToken);
        }
        return "";
    },
    Is.EqualTo(expectedContent)
        .After(timeouts.AssertionTimeoutInMs)
        .MilliSeconds.PollEvery(TestTimeouts.PollingIntervalInMs)
        .MilliSeconds
);
```

**File/Directory Existence:**

```csharp
Assert.That(
    () => File.Exists(filePath),
    Is.True
        .After(timeouts.AssertionTimeoutInMs)
        .MilliSeconds.PollEvery(TestTimeouts.PollingIntervalInMs)
        .MilliSeconds
);
```

**Log Message Verification:**

```csharp
Assert.That(
    () => host.LogEntries,
    Has.One.Matches<string>(msg => msg.Contains(expectedMessage, StringComparison.OrdinalIgnoreCase))
        .After(timeouts.AssertionTimeoutInMs)
        .MilliSeconds.PollEvery(TestTimeouts.PollingIntervalInMs)
        .MilliSeconds
);
```

**stdout / stderr Verification:**

```csharp
Assert.That(
    () => host.GetStdout(), // or .GetStderr
    Does.Contain(expectedMessage))
        .After(timeouts.AssertionTimeoutInMs)
        .MilliSeconds.PollEvery(TestTimeouts.PollingIntervalInMs)
        .MilliSeconds
);
```

#### Common Test Issues and Solutions

**File System Timing**: Always use polling assertions since file system operations are asynchronous
**Resource Leaks**: Ensure proper disposal with `using` statements
**Path Handling**: Use `Path.Combine()` for cross-platform path construction

## Development Style

- we use vertical slices to create code with high cohesion
	- most changes you will do are going to affect only a single slice, but sometimes more than one slice (or the `SharedKernel`) needs to be updated
	- you should almost never need to touch the code in `Core`; if you think you do need to change something there, stop and ask the user for confirmation about the proposed change
- we are using Test-Driven Development (TDD)
- all tests are end-to-end tests which execute the app by invoking it like a user would
- after any change, we run `dotnet test` to ensure that the application builds and that all tests succeed
- you must continue making changes until the feature is fully implemented and all tests succeed
- when a build produces errors due to analyzers (e.g. because of a missing newline at the end of a file), you MUST run `just fix` to attempt to automatically correct the code, then run `just build` again, and fix any remaining issues which could not be fixed automatically
- each vertical slice has a `REQUIREMENTS.md` file which can be referenced to understand the desired behavior
- each vertical slice has an `ARCHITECTURE.md` file which should be updated as part of the implementation of any change

To be clear, the plan for any implementation MUST use the TDD approach, and the plan should roughly consist of the following steps (sometimes more, sometimes less, depending on the complexity of the feature):

1. determine if there is a suitable existing vertical slice that the requirement fits into, and if not, then define a new vertical slice
2. ensure that there is a `REQUIREMENTS.md` file for the target slice and that the file is updated to reflect the request from the user; if you determine that the document does not exist or is not up to date, stop processing and prompt the user to let you create or update this file before continuing
3. if the feature is more complex, ensure that there is a detailed implementation plan for it in `.plans` and if not, prompt the user to let you create this plan before continuing
4. define the API for the new requirement (e.g. a CliFx command, etc.); note that some requirements do not require new APIs to be added, just existing logic to be extended
5. define a list of test cases for the new feature
6. implement the test cases against new or existing APIs to cover all success and failure cases; in our case this usually means invoking the whole program with the correct command line arguments
7. run the tests to assert that they are all failing (i.e. run `just test`)
8. write the implementation to make the tests succeed; during this step you may extract code into the `SharedKernel` if necessary
9. run the tests to assert that they are all succeeding
10. refactor the code as necessary to improve its quality attributes like security, performance, reliability, maintainability, etc.
11. format the code according to our guidelines (i.e. run `just format`)
12. ensure that all tests are still successful (i.e. run `just test`); this is a MUST, it is not acceptable for any test to be failing, i.e. your work is not considered finished until all tests pass
13. build the project in release mode to ensure that there are no issues that were only warnings during development (i.e. run `just build-release`)
14. update (or create) the vertical slice's `ARCHITECTURE.md` to reflect the implementation

## Code Style

### General

- we end each text file (e.g. `.cs`, `.md`, etc.) with a new line

### CSharp

- we end the file with a blank line
- we use top-level namespaces everywhere
- we place `using` statements outside the namespace, and we omit the prefix `[MyProject].` from `using` statements when referencing other vertical slices
	- there is no need to add `using` statements for `Core` or `SharedKernel` since those are globally imported in `GlobalUsings.cs`
- we use the Allman braces style
- we remove any unused imports
- we always use braces around any `if`, `for`, `while`, etc. statements
- all classes are by default `internal` and `sealed` (except test fixtures)
- for classes, we prefer primary constructors wherever possible
- we always use `var` instead of the explicit type name when declaring variables
- we prefer `using var` and `await using var` over `using` blocks
- we usually do not log explicitly in message and signal handlers and instead we rely on the logging middlewares on the pipelines
- we use pattern matching for things like `null` checks or comparing a variable to enum values, etc.
- we do not introduce interfaces unnecessarily for implementation classes, since we test our program through invoking it like a user would use the app, and therefore don't need interfaces for mocking classes for testing
- naming style
	- class, record, and struct names: PascalCase
	- interface names: IPascalCase
	- fields: _camelCase
	- properties: PascalCase
	- method names: PascalCase

### Markdown

- markdown files should always have a blank line between any section header (i.e. lines starting with `#`) and the content
- markdown files should always have blank lines before and after any lists
- markdown files should always have a language tag for code blocks; if the block contains no code, just informational output, use `txt` as the tag

## Available Commands

??

## Documentation Templates

In the `.docs` directory you can find template files for the different kinds of documentations we create. Whenever you need to create or update a documentation file, you can check the template for reference. For example, when creating a `REQUIREMENTS.md` file for a vertical slice, the document should be roughly based on `.docs/REQUIREMENTS.template.md`. The same goes for `ARCHITECTURE.md` and `.docs/ARCHITECTURE.template.md`.

When you are asked to develop an implementation plan, you can use `.docs/PLAN.template.md` as a template.