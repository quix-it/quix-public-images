FROM sonarsource/sonar-scanner-cli:4
FROM maven:3.9-eclipse-temurin-21

RUN mkdir -p /repo $MAVEN_CONFIG && \
    apt-get update && apt-get install -y gettext git jq

COPY --from=0 /opt/sonar-scanner /opt/sonar-scanner

ENV PATH=$PATH:/opt/sonar-scanner/bin
ENV MAVEN_OPTS="-Dhttps.protocols=TLSv1.2 -Dorg.slf4j.simpleLogger.showDateTime=true -Djava.awt.headless=true"

# Mitigazione Java4Shell (CVE-2026-114938): disattiva l'intrinsic Base64 AVX-512 difettoso.
# Rimuovere quando l'immagine base include una JDK con la patch del 17/11/2026.
ENV JAVA_TOOL_OPTIONS="-XX:-UseBASE64Intrinsics"
