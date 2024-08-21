FROM sonarsource/sonar-scanner-cli:4
FROM maven:3.8-openjdk-17

RUN mkdir -p /repo $MAVEN_CONFIG && \
    apt-get update && apt-get install -y gettext git jq

COPY --from=0 /opt/sonar-scanner /opt/sonar-scanner

ENV PATH=$PATH:/opt/sonar-scanner/bin
ENV MAVEN_OPTS="-Dhttps.protocols=TLSv1.2 -Dorg.slf4j.simpleLogger.showDateTime=true -Djava.awt.headless=true"
