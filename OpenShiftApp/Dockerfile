FROM microsoft/dotnet:2.0-aspnetcore-runtime AS base
WORKDIR /app
COPY ./publish .
ENTRYPOINT [“dotnet”, “OpenShiftApp.dll”]