# ���������� ������� ����� � ASP.NET 8.0
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base

# ������������� ������� ���������� ������ ����������
WORKDIR /app

# ���������� SDK
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

# �������� ����� � ���������
COPY . /src

# ������������� ������� ���������� ������ ����������
WORKDIR /src
# ������������� ����������� ���������� � ��������� ����������
RUN ls
RUN dotnet restore
RUN dotnet build "./7_Calculator.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "./7_Calculator.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish ./

# ���������� ������� ������� ����������
ENTRYPOINT ["dotnet", "7_Calculator.dll"]
