FROM node:14
FROM sonarsource/sonar-scanner-cli:latest

ENV NG_CLI_ANALYTICS=ci
ENV WORKDIR=/workdir
ENV PS1='\u@\h:\w\$ '

COPY --from=0 /usr/local/bin/node* /usr/local/bin/

USER root

RUN useradd -m -d $WORKDIR -u 1001 node

WORKDIR $WORKDIR

RUN dnf install -y gettext jq tar && dnf clean all

RUN npm update && \
    npm install -g @angular/cli@11.1.0 @angular-devkit/build-angular

RUN rm -rf ..?* .[!.]* *

ENTRYPOINT [ "/bin/bash" ]
