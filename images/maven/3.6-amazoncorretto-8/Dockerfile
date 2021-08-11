FROM maven:3.6-amazoncorretto-8

RUN mkdir -p /repo $MAVEN_CONFIG && \
    yum install -y gettext git jq

ENV MAVEN_OPTS="-Dhttps.protocols=TLSv1.2 -Dorg.slf4j.simpleLogger.showDateTime=true -Djava.awt.headless=true"
