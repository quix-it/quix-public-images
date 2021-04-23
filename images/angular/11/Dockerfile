FROM node:14

RUN npm install -g @angular/cli@11.1.0

ENV WORKDIR=/workspace
WORKDIR $WORKDIR
RUN chmod 777 .

USER node

ENTRYPOINT [ "/bin/bash" ]