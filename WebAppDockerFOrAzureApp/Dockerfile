FROM mcr.microsoft.com/dotnet/sdk AS build

WORKDIR /code
COPY ["./WebAppDockerFOrAzureApp/WebAppFOrAzureApp.csproj", "./"]
RUN dotnet restore 
COPY . .
RUN dotnet publish --output /output --configuration Release

FROM mcr.microsoft.com/dotnet/aspnet:5.0.0
COPY --from=build /output /app

WORKDIR /app

ENTRYPOINT [ "dotnet", "WebAppFOrAzureApp.dll"]
