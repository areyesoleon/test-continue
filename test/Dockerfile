FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
EXPOSE 6050
EXPOSE 80
COPY test.csproj .
RUN dotnet restore "test.csproj"
COPY . .
RUN dotnet publish "test.csproj" -c Release -o /publish

FROM mcr.microsoft.com/dotnet/aspnet:7.0 as final
WORKDIR /app
COPY --from=build /publish .
ENTRYPOINT [ "dotnet", "test.dll" ]
