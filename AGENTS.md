# Repository Guidelines

## Project Structure & Module Organization
- `CodexTestApp1.sln` is the entry point for the solution; open it in Visual Studio or run `dotnet` commands from the repository root.
- Application code lives in `CodexTestApp1/Program.cs`. Keep new classes under `CodexTestApp1/` in logically named folders (for example, `CodexTestApp1/Services/`).
- Build outputs (`bin/`) and intermediate artifacts (`obj/`) are generated automatically; do not commit them.

## Build, Test, and Development Commands
- `dotnet restore CodexTestApp1/CodexTestApp1.csproj` — restores NuGet packages.
- `dotnet build CodexTestApp1/CodexTestApp1.csproj` — compiles the application and validates there are no build-time warnings or errors.
- `dotnet run --project CodexTestApp1/CodexTestApp1.csproj` — runs the console app locally.
- `dotnet test` — executes all tests once they are added; ensure it succeeds before opening a pull request.

## Coding Style & Naming Conventions
- Follow standard C# conventions: PascalCase for classes and public members, camelCase for locals and parameters, and `_camelCase` for private fields.
- Default indentation is four spaces; avoid tabs.
- Run `dotnet format CodexTestApp1/CodexTestApp1.csproj` before submitting to enforce consistent formatting and resolve analyzer warnings when applicable.

## Testing Guidelines
- Prefer xUnit for new test projects; place them under `CodexTestApp1.Tests/`.
- Name test classes after the class under test (`ProgramTests`) and methods using `MethodName_ShouldExpectedBehavior`.
- Maintain high branch coverage on critical logic paths; add regression tests for each bug fix.
- Execute `dotnet test` locally and ensure failing tests are resolved before pushing changes.

## Commit & Pull Request Guidelines
- Use present-tense, descriptive commit messages such as `Add menu option for bulk import`.
- Group related changes into a single commit; avoid mixing refactors with feature work.
- Pull requests must include a summary of changes, testing evidence (`dotnet test` output or manual steps), linked work items, and screenshots or console output when UI/CLI behavior changes.
- Request review from a teammate and wait for CI to pass before merging.

## Security & Configuration Tips
- Store secrets and environment-specific values outside the repository (for example, user secrets via `dotnet user-secrets` or environment variables).
- Review dependencies regularly; update outdated NuGet packages with `dotnet list package --outdated`.
