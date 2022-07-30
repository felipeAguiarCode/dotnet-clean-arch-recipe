# Create project

Recipe to create a clean arch based project By Felipe Aguiar

## Create Folders Structure

```bash
    mkdir src
    mkdir -p src/Infrastructure, src/Domain
    mkdir -p src/Application, src/WebApi
```

## Create Projects

```bash
    dotnet new classlib --output "src/Domain" --name "Domain"
    dotnet new classlib --output "src/Application" --name "Application"
    dotnet new classlib --output "src/Infrastructure" --name "Infra"
    dotnet new webapi --output "src/WebApi" --name "WebApi"
```

## Create Solution

```bash
    dotnet new sln --output "src" --name "CleanApi"
    dotnet sln src/CleanApi.sln add src/Application/Application.csproj
    dotnet sln src/CleanApi.sln add src/Domain/Domain.csproj
    dotnet sln src/CleanApi.sln add src/Infrastructure/Infra.csproj
    dotnet sln src/CleanApi.sln add src/WebApi/WebApi.csproj
```

## Add References

```bash
    dotnet add src/Application/Application.csproj reference src/Domain/domain.csproj

    dotnet add src/Infrastructure/Infra.csproj reference src/Application/Application.csproj

    dotnet add src/WebApi/UI.csproj reference src/Application/Application.csproj
    dotnet add src/WebApi/UI.csproj reference src/Domain/domain.csproj
    dotnet add src/WebApi/UI.csproj reference src/Infrastructure/Infra.csproj
```

# Domain

This will contain all entities, enums, exceptions, interfaces, types and logic specific to the domain layer.

# Application

This layer contains all application logic. It is dependent on the domain layer, but has no dependencies on any other layer or project. This layer defines interfaces that are implemented by outside layers. For example, if the application need to access a notification service, a new interface would be added to application and an implementation would be created within infrastructure.

# Infrastructure

This layer contains classes for accessing external resources such as file systems, web services, database, smtp, and so on. These classes should be based on interfaces defined within the application layer.

# WebApi

This layer is a public layer to serve a external client

## To Remove

dotnet remove app/app.csproj reference \*_/_.csproj`
