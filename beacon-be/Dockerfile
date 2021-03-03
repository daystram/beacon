FROM mcr.microsoft.com/dotnet/sdk:5.0 AS builder
WORKDIR /build
COPY *.csproj ./
RUN dotnet restore
COPY . ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /app
COPY --from=builder /build/out .
ENTRYPOINT ["dotnet", "beacon-be.dll"]