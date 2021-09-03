FROM maven:3.8-amazoncorretto-11

RUN mkdir -p /repo $MAVEN_CONFIG && \
    yum install -y gettext git jq

ENV MAVEN_OPTS="-Dhttps.protocols=TLSv1.2 -Dorg.slf4j.simpleLogger.showDateTime=true -Djava.awt.headless=true"
