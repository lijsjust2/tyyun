FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

COPY CtYun.csproj .
RUN dotnet restore

COPY . .
RUN dotnet publish -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/runtime:8.0 AS base
WORKDIR /app

COPY --from=build /app/publish/ ./

ENV CTYUN_DATA_DIR=/app/data

VOLUME ["/app/data"]

ENTRYPOINT ["dotnet", "CtYun.dll"]
