FROM sonarsource/sonar-scanner-cli:4
FROM node:14

COPY --from=0 /opt/sonar-scanner /opt/sonar-scanner

ENV PATH=$PATH:/opt/sonar-scanner/bin
ENV NG_CLI_ANALYTICS=ci
ENV WORKDIR=/workspace

RUN apt update && \
    apt install -y gettext

RUN npm update && \
    npm install -g @angular/cli@12.1.0

WORKDIR $WORKDIR
RUN chmod 777 .

# RUN groupmod -g 1001 node && usermod -u 1001 node
# USER node

ENTRYPOINT [ "/bin/bash" ]
