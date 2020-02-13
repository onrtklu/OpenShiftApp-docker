FROM microsoft/aspnetcore:2.0 AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/aspnetcore-build:2.0 AS build
WORKDIR /src
COPY ["OpenShiftApp/OpenShiftApp.csproj", "OpenShiftApp/"]
RUN dotnet restore "OpenShiftApp/OpenShiftApp.csproj"
COPY . .
WORKDIR "/src/OpenShiftApp"
RUN dotnet build "OpenShiftApp.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "OpenShiftApp.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "OpenShiftApp.dll"]