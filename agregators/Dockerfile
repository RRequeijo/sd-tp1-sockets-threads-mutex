#Docker file do agregador
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

COPY . . 
RUN dotnet restore
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /app/out .

# Usa variáveis de ambiente passadas no docker-compose
ENV ASPNETCORE_ENVIRONMENT=Production

ENTRYPOINT ["dotnet", "agregators.dll"]
