FROM microsoft/aspnetcore:2.0-nanoserver-sac2016 AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/aspnetcore-build:2.0-nanoserver-sac2016 AS build
WORKDIR /src
COPY Array-Reversing-Api/Array-Reversing-Api.csproj Array-Reversing-Api/
RUN dotnet restore Array-Reversing-Api/Array-Reversing-Api.csproj
COPY . .
WORKDIR /src/Array-Reversing-Api
RUN dotnet build Array-Reversing-Api.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish Array-Reversing-Api.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "Array-Reversing-Api.dll"]
