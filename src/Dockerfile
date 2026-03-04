# -----------------------------
# Stage 1: Build Stage
# -----------------------------
FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR /src

# Copy csproj and restore dependencies first (better caching)
COPY cartservice.csproj .
RUN dotnet restore cartservice.csproj

# Copy remaining source code
COPY . .

# Publish the application
RUN dotnet publish cartservice.csproj -c Release -o /app/publish


# -----------------------------
# Stage 2: Runtime Stage
# -----------------------------
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app

# Copy published output from build stage
COPY --from=build /app/publish .

# Expose port (change if your app uses different port)
EXPOSE 8080

# Run the application
ENTRYPOINT ["dotnet", "cartservice.dll"]