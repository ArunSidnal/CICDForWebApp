FROM mcr.microsoft.com/dotnet/sdk:5.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build

WORKDIR /src
COPY ["./WebAppDockerFOrAzureApp/WebAppFOrAzureApp.csproj", "./"]
RUN dotnet restore "./WebAppFOrAzureApp.csproj"
COPY . .
RUN dotnet build "./WebAppFOrAzureApp.csproj" -c Release -o /app/build

FROM build as publish
RUN dotnet publish "./WebAppFOrAzureApp.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
CMD dotnet "WebAppFOrAzureApp"