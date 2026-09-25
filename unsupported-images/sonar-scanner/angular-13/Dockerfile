FROM node:14
# sonar-scanner-cli 12.2.0.4256_8.1.0
FROM sonarsource/sonar-scanner-cli@sha256:a3f4215076706c95a17a68c19322ee916e40a3acd081a8c1a1e839e0194afa57

ENV NG_CLI_ANALYTICS=ci
ENV WORKDIR=/workdir
ENV PS1='\u@\h:\w\$ '

COPY --from=0 /usr/local/bin/node* /usr/local/bin/

USER root

RUN useradd -m -d $WORKDIR -u 1001 node

WORKDIR $WORKDIR

RUN dnf install -y gettext jq tar findutils && dnf clean all

RUN npm update && \
    npm install -g @angular/cli@13.1.0 @angular-devkit/build-angular

RUN rm -rf ..?* .[!.]* *

ENTRYPOINT [ "/bin/bash" ]
