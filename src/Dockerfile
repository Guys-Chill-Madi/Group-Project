FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR /src
COPY cartservice.csproj .
RUN dotnet restore cartservice.csproj
COPY . .
RUN dotnet publish cartservice.csproj -c Release -o /app/publish
FROM mcr.microsoft.com/dotnet/aspnet:10.0
WORKDIR /app
COPY --from=build /app/publish .
EXPOSE 7070
ENTRYPOINT ["dotnet", "cartservice.dll"]
