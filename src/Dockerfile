FROM mcr.microsoft.com/dotnet/aspnet:6.0-alpine AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk:6.0-alpine AS build
WORKDIR /src
COPY . .

FROM build AS publish
RUN dotnet restore
RUN dotnet publish "src/ProjectTemplate.Api/ProjectTemplate.Api.csproj" -c Release -o /out

FROM base AS final
WORKDIR /app
COPY --from=publish /out .
ENTRYPOINT ["dotnet", "ProjectTemplate.Api.dll"] 