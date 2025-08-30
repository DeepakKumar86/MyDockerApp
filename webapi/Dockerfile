# Build stage
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY . .

WORKDIR /src/webapi
RUN dotnet publish -c Release -o /app/publish

# Runtime stage
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
EXPOSE 8080
ENV ASPNETCORE_URLS=http://+:8080
COPY --from=build /app/publish .



#ENTRYPOINT → Defines the default executable for the container.
#["dotnet", "webapi.dll"] → This is the command (in exec form):
#dotnet → Runs the .NET runtime.
#webapi.dll → Your application’s compiled .NET Core Web API DLL file.
ENTRYPOINT ["dotnet", "webapi.dll"]