FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /src
COPY Ignite2018PreConfWorkshop/Ignite2018PreConfWorkshop.csproj Ignite2018PreConfWorkshop/
RUN dotnet restore Ignite2018PreConfWorkshop/Ignite2018PreConfWorkshop.csproj
COPY . .
WORKDIR /src/Ignite2018PreConfWorkshop
RUN dotnet build Ignite2018PreConfWorkshop.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish Ignite2018PreConfWorkshop.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "Ignite2018PreConfWorkshop.dll"]
