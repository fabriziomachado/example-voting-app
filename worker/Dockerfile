# FROM mcr.microsoft.com/dotnet/core/sdk:3.1 as builder
FROM mcr.microsoft.com/dotnet/core/sdk:2.1-alpine as builder

WORKDIR /Worker
COPY src/Worker/Worker.csproj .
RUN dotnet restore

COPY src/Worker/ .
RUN dotnet publish -c Release -o /out Worker.csproj

# app image
# FROM mcr.microsoft.com/dotnet/core/runtime:3.1
FROM mcr.microsoft.com/dotnet/core/aspnet:2.1-alpine

WORKDIR /app
ENTRYPOINT ["dotnet", "Worker.dll"]

COPY --from=builder /out .