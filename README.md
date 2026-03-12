# Accelerator MAUI Application

A .NET MAUI solution structured in multiple layers for cross-platform mobile and desktop development.

## Solution Structure

| Project | Layer | Description |
|---|---|---|
| Accelerator.Application | Application | Main MAUI application |
| Accelerator.DemoApp | Application | Demo MAUI application |
| Accelerator.Business | Business | Business logic layer |
| Accelerator.DataAccess | Infrastructure | Data access layer |
| Accelerator.ExternalServices | Infrastructure | External service integrations |
| Accelerator.Contracts | Crosscutting | DTOs and contracts |
| Accelerator.Entities | Crosscutting | Domain entities |
| Accelerator.Utils | Crosscutting | Shared utilities |
| Accelerator.UnitedTest | Tests | Unit tests |

## Requirements

- [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0)
- .NET MAUI workload: `dotnet workload install maui`
- Visual Studio 2022 17.12+ or JetBrains Rider 2024.3+

## Getting Started

```bash
# Install the MAUI workload
dotnet workload install maui

# Restore dependencies
dotnet restore Accelerator.Application.sln

# Build the solution
dotnet build Accelerator.Application.sln

# Run tests
dotnet test Accelerator.Application.sln
```

## Migration: .NET 8 → .NET 10

### Summary of Changes

The solution was migrated from .NET 8 to .NET 10 to take advantage of improved performance, extended support, and the latest framework features.

### Updated Target Frameworks

All projects were updated from `net8.0-*` to `net10.0-*`:

| Platform | Before | After |
|---|---|---|
| Android | `net8.0-android` | `net10.0-android` |
| iOS | `net8.0-ios` | `net10.0-ios` |
| Mac Catalyst | `net8.0-maccatalyst` | `net10.0-maccatalyst` |
| Windows | `net8.0-windows10.0.19041.0` | `net10.0-windows10.0.19041.0` |

### Updated NuGet Dependencies

| Package | Before | After |
|---|---|---|
| `Microsoft.Extensions.Logging.Debug` | 8.0.0 | 10.0.0 |
| `Microsoft.Maui.Controls` | Resolved via SDK (net8.0) | Resolved via SDK (net10.0) |
| `Microsoft.Maui.Controls.Compatibility` | Resolved via SDK (net8.0) | Resolved via SDK (net10.0) |

### Breaking Changes

No breaking changes were identified for this solution during the migration. The MAUI API surface remains compatible between .NET 8 and .NET 10.

### CI/CD Pipeline

A GitHub Actions workflow (`.github/workflows/dotnet.yml`) was added to:
- Build the solution using .NET 10 SDK on every push/pull request to `main`
- Run automated tests
- Install the required MAUI workload automatically
