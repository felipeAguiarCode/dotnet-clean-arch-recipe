## Building scripts

You'll need [dotnet-sdk](https://dotnet.microsoft.com/en-us/download) installed on your computer in order to build this app.

Recipe to create a clean arch based project

### 🔧 Create Folders Structure

```bash
    mkdir src
    mkdir -p src/Infrastructure, src/Domain
    mkdir -p src/Application, src/WebApi
```

### 🔧 Create Projects

```cs
    dotnet new classlib --output "src/Domain" --name "Domain"
    dotnet new classlib --output "src/Application" --name "Application"
    dotnet new classlib --output "src/Infrastructure" --name "Infra"
    dotnet new webapi --output "src/WebApi" --name "WebApi"
```

### 🔧 Create Solution and add projects

```cs
    dotnet new sln --output "src" --name "CleanApi"
    dotnet sln src/CleanApi.sln add src/Application/Application.csproj
    dotnet sln src/CleanApi.sln add src/Domain/Domain.csproj
    dotnet sln src/CleanApi.sln add src/Infrastructure/Infra.csproj
    dotnet sln src/CleanApi.sln add src/WebApi/WebApi.csproj
```

### 🔧 Add References

```cs
    dotnet add src/Application/Application.csproj reference src/Domain/domain.csproj

    dotnet add src/Infrastructure/Infra.csproj reference src/Application/Application.csproj

    dotnet add src/WebApi/WebApi.csproj reference src/Application/Application.csproj
    dotnet add src/WebApi/WebApi.csproj reference src/Domain/domain.csproj
    dotnet add src/WebApi/WebApi.csproj reference src/Infrastructure/Infra.csproj
```

## To Remove

dotnet remove app/app.csproj reference \*_/_.csproj`
