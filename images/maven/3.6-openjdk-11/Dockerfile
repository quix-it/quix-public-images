FROM sonarsource/sonar-scanner-cli:4
FROM maven:3.6-openjdk-11

# Buster's live apt mirrors were pruned after EOL; switch to the
# snapshot.debian.org sources already baked into this base image so the
# exact same package versions remain fetchable.
RUN sed -i \
      -e '/^deb /d' \
      -e 's|^# *deb |deb |' \
      /etc/apt/sources.list && \
    echo 'Acquire::Check-Valid-Until "false";' > /etc/apt/apt.conf.d/99no-check-valid-until

RUN mkdir -p /repo $MAVEN_CONFIG && \
    apt-get update && apt-get install -y gettext git jq

COPY --from=0 /opt/sonar-scanner /opt/sonar-scanner

ENV PATH=$PATH:/opt/sonar-scanner/bin
ENV MAVEN_OPTS="-Dhttps.protocols=TLSv1.2 -Dorg.slf4j.simpleLogger.showDateTime=true -Djava.awt.headless=true"
