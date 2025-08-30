# Single-stage build
FROM mcr.microsoft.com/dotnet/sdk:8.0

# Set working directory
WORKDIR /app

# Copy all source code
COPY . .

# Publish the application
WORKDIR /app/webapi
RUN dotnet publish -c Release -o /app/publish

# Set working directory for runtime
WORKDIR /app/publish

# Expose port
EXPOSE 8080
ENV ASPNETCORE_URLS=http://+:8080

# Run the application
ENTRYPOINT ["dotnet", "webapi.dll"]