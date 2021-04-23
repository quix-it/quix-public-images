FROM node:14

RUN npm install -g @angular/cli@9.1.6

ENV WORKDIR=/workspace
WORKDIR $WORKDIR
RUN chmod 777 .

USER node

ENTRYPOINT [ "/bin/bash" ]