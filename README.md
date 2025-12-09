# Rent-A-Car Application

A modern, scalable Rent-A-Car management system built with .NET 9 and Clean Architecture principles.

## Overview

This project is a comprehensive car rental platform featuring a well-architected multi-layered application. It demonstrates best practices in enterprise application development using .NET 9, including clean architecture, domain-driven design, and CQRS patterns.

## Technology Stack

- **Framework**: .NET 9
- **Web API**: ASP.NET Core
- **Database**: SQL Server with Entity Framework Core
- **Caching**: Redis (StackExchange.Redis)
- **Logging**: Serilog with file and database sinks
- **API Documentation**: Swagger/OpenAPI
- **Dynamic Queries**: System.Linq.Dynamic.Core

## Project Structure

The solution is organized following Clean Architecture principles:

```
RentACar/
├── WebApi/               # Web API layer - ASP.NET Core application
├── Application/          # Business logic and application services
├── Domain/              # Domain entities and business rules
├── Persistence/         # Data access and database configuration
├── Infrastructure/      # External service integrations
└── Core.Application/    # Core application framework (reference)
```

### Layer Responsibilities

- **WebApi**: HTTP endpoints, controllers, API configuration, and Swagger setup
- **Application**: Use cases, application services, DTOs, and business logic
- **Domain**: Core business entities, value objects, and domain rules
- **Persistence**: Entity Framework Core configurations, repositories, and database context
- **Infrastructure**: External services, third-party integrations

## Key Features

- **RESTful API** with well-structured controllers
- **Dynamic Querying** support for flexible data retrieval
- **Comprehensive Logging** using Serilog to file and database
- **Caching Layer** with Redis for performance optimization
- **Database Migrations** support with Entity Framework Core Tools
- **API Documentation** with Swagger/OpenAPI
- **Nullable Reference Types** enabled for safer code

## Getting Started

### Prerequisites

- .NET 9 SDK or later
- SQL Server (local or remote)
- Redis (optional, for caching features)

### Installation

1. Clone the repository
   ```bash
   git clone <repository-url>
   cd RentACar
   ```

2. Restore NuGet packages
   ```bash
   dotnet restore
   ```

3. Configure the database connection string in `appsettings.json` (WebApi project)

4. Apply database migrations
   ```bash
   dotnet ef database update --project Persistence --startup-project WebApi
   ```

5. Build the solution
   ```bash
   dotnet build
   ```

6. Run the API
   ```bash
   dotnet run --project WebApi
   ```

The API will be available at `https://localhost:5001` (or the configured port).

## API Documentation

Once the application is running, access the Swagger UI at:
- **Swagger UI**: `https://localhost:5001/swagger/index.html`
- **OpenAPI JSON**: `https://localhost:5001/swagger/v1/swagger.json`

## Current Endpoints

- **Models Controller**: Manage car models
  - `GET /api/models` - Get all models
  - `POST /api/models` - Create a new model

- **Brands Controller**: Manage car brands
  - `GET /api/brands` - Get all brands
  - `POST /api/brands` - Create a new brand

## Configuration

### Logging

Serilog is configured to write logs to:
- Local file system
- SQL Server database

Configure logging settings in `Program.cs` or `appsettings.json`.

### Caching

Redis caching is integrated for performance optimization. Configure Redis connection in the application settings.

### Database

Entity Framework Core is used for data access with SQL Server. Migrations can be managed using:
```bash
dotnet ef migrations add <MigrationName> --project Persistence
dotnet ef database update --project Persistence
```

## Development

### Building
```bash
dotnet build
```

### Running Tests (if available)
```bash
dotnet test
```

### Database Migrations
```bash
# Create a new migration
dotnet ef migrations add <MigrationName> --project Persistence --startup-project WebApi

# Apply migrations
dotnet ef database update --project Persistence --startup-project WebApi

# Remove the last migration
dotnet ef migrations remove --project Persistence --startup-project WebApi
```

## Architecture Principles

This project implements:

- **Clean Architecture**: Clear separation of concerns across layers
- **SOLID Principles**: Maintainable and extensible code
- **Dependency Injection**: Loosely coupled components
- **Entity Framework Core**: ORM for data persistence
- **Repository Pattern**: Abstraction over data access

## Dependencies

Key NuGet packages used:

| Package | Version | Purpose |
|---------|---------|---------|
| Microsoft.AspNetCore.OpenApi | 9.0.11 | OpenAPI support |
| Microsoft.EntityFrameworkCore.Tools | 9.0.16 | EF Core migrations |
| Microsoft.Extensions.Caching.StackExchangeRedis | 9.0.16 | Redis caching |
| Serilog | 4.3.1 | Structured logging |
| Swashbuckle.AspNetCore | 9.0.6 | Swagger/OpenAPI documentation |
| System.Linq.Dynamic.Core | 1.7.2 | Dynamic LINQ queries |

---

**Built with .NET 9 | Clean Architecture | Enterprise-Ready**
