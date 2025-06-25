# المرحلة 1: Build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# انسخ ملفات المشروع
COPY . ./

# Restore الـ NuGet packages
RUN dotnet restore

# Build and publish المشروع
RUN dotnet publish MedBridge.csproj -c Release -o /app/publish

# المرحلة 2: Runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app

# انسخ الـ publish output
COPY --from=build /app/publish .

# شغل التطبيق
ENTRYPOINT ["dotnet", "MedBridge.dll"]
