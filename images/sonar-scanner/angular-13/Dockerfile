FROM node:14
FROM sonarsource/sonar-scanner-cli:4

ENV NG_CLI_ANALYTICS=ci
ENV WORKDIR=/workdir
ENV PS1='\u@\h:\w\$ '

COPY --from=0 /usr/local/bin/node* /usr/local/bin/

RUN adduser -D -h $WORKDIR -u 1001 node

WORKDIR $WORKDIR

RUN apk update &&\
    apk add gettext jq && \
    apk add --no-cache tar

RUN npm update && \
    npm install -g @angular/cli@13.1.0 @angular-devkit/build-angular

RUN rm -rf ..?* .[!.]* *

# USER node 

ENTRYPOINT [ "/bin/bash" ]
