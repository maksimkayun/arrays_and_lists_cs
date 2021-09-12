FROM mcr.microsoft.com/dotnet/runtime:5.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["Arrays and lists/Arrays and lists.csproj", "Arrays and lists/"]
RUN dotnet restore "Arrays and lists/Arrays and lists.csproj"
COPY . .
WORKDIR "/src/Arrays and lists"
RUN dotnet build "Arrays and lists.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Arrays and lists.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Arrays and lists.dll"]
