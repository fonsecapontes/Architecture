# DotNet
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS dotnet
COPY src ./source
RUN dotnet publish ./source/Architecture.Api/Architecture.Api.csproj --configuration Release --output /dist

# Runtime
FROM mcr.microsoft.com/dotnet/aspnet:7.0
ENV DOTNET_SYSTEM_GLOBALIZATION_INVARIANT=false
WORKDIR /app
COPY --from=dotnet /dist .
ENTRYPOINT ["dotnet", "Architecture.Api.dll"]