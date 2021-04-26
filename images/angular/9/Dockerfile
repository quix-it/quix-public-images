FROM node:14

ENV NG_CLI_ANALYTICS=ci
ENV WORKDIR=/workspace

RUN apt update && \
    apt install -y gettext

RUN npm update && \
    npm install -g @angular/cli@9.1.6

WORKDIR $WORKDIR
RUN chmod 777 .

RUN groupmod -g 1001 node && usermod -u 1001 node
USER node

ENTRYPOINT [ "/bin/bash" ]
