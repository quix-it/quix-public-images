FROM sonarsource/sonar-scanner-cli:4
FROM maven:3.6-openjdk-11

RUN mkdir -p /repo $MAVEN_CONFIG && \
    yum install -y gettext git jq

COPY --from=0 /opt/sonar-scanner /opt/sonar-scanner

ENV PATH=$PATH:/opt/sonar-scanner/bin
ENV MAVEN_OPTS="-Dhttps.protocols=TLSv1.2 -Dorg.slf4j.simpleLogger.showDateTime=true -Djava.awt.headless=true"
