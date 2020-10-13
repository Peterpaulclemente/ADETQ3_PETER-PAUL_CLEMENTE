#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /src
COPY ["ADETQ3_PETER-PAUL_CLEMENTE/ADETQ3_PETER-PAUL_CLEMENTE.csproj", "ADETQ3_PETER-PAUL_CLEMENTE/"]
RUN dotnet restore "ADETQ3_PETER-PAUL_CLEMENTE/ADETQ3_PETER-PAUL_CLEMENTE.csproj"
COPY . .
WORKDIR "/src/ADETQ3_PETER-PAUL_CLEMENTE"
RUN dotnet build "ADETQ3_PETER-PAUL_CLEMENTE.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "ADETQ3_PETER-PAUL_CLEMENTE.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "ADETQ3_PETER-PAUL_CLEMENTE.dll"]