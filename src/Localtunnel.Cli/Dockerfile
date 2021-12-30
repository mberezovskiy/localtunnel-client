FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app

COPY src/Localtunnel/Localtunnel.csproj /app/src/Localtunnel/
COPY src/Localtunnel.Cli/Localtunnel.Cli.csproj /app/src/Localtunnel.Cli/
COPY Localtunnel.sln /app/

RUN dotnet restore

COPY . .

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/runtime:6.0
WORKDIR /app

COPY --from=build /app/out .
RUN chmod +x Localtunnel.Cli

ENTRYPOINT ["/app/Localtunnel.Cli"]
