FROM mcr.microsoft.com/dotnet/core/sdk:2.1 AS build-env
WORKDIR /app

# Copy from the publish
COPY ./bin/Debug/netcoreapp2.1/publish /app/out

# Copy the Angular app
COPY ./wwwroot /app/out/wwwroot

# Build runtime image
FROM mcr.microsoft.com/dotnet/core/aspnet:2.1
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "Spark.Web.dll"]
