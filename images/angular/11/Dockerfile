FROM node:14

ENV NG_CLI_ANALYTICS=ci
ENV WORKDIR=/workspace

RUN apt update && \
    apt install -y gettext

RUN npm update && \
    npm install -g @angular/cli@11.1.0

WORKDIR $WORKDIR
RUN chmod 777 .

USER node

ENTRYPOINT [ "/bin/bash" ]
