# FROM microsoft/dotnet:2.1-sdk-nanoserver-sac2016 as builder
FROM mcr.microsoft.com/dotnet/core/sdk:2.1-alpine as builder

WORKDIR /Result
COPY Result/Result.csproj .
RUN dotnet restore

COPY /Result .
RUN dotnet publish -c Release -o /out Result.csproj

# app image
# FROM microsoft/dotnet:2.1-aspnetcore-runtime-nanoserver-sac2016
FROM mcr.microsoft.com/dotnet/core/aspnet:2.1-alpine

WORKDIR /app
ENTRYPOINT ["dotnet", "Result.dll"]

COPY --from=builder /out .