FROM microsoft/dotnet:2.2-sdk as build

ARG BUILDCONFIG=RELEASE
ARG VERSION=1.0.0
ARG CSPROJNAME=BITAD_QrCode.csproj

COPY $CSPROJNAME /build/

RUN dotnet restore ./build/$CSPROJNAME

COPY . ./build/
WORKDIR /build/
RUN dotnet publish ./$CSPROJNAME -c $BUILDCONFIG -o out /p:Version=$VERSION

FROM microsoft/dotnet:2.2-aspnetcore-runtime
WORKDIR /app

COPY --from=build /build/out .
ENTRYPOINT ["dotnet", "BITAD_QrCode.dll"]