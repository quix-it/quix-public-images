FROM alpine:3

RUN apk update && \ 
    apk add --no-cache git bash gettext jq curl grep yq

RUN mkdir -p /workdir

ENV WORKDIR=/workdir

WORKDIR $WORKDIR

RUN rm -rf ..?* .[!.]* *

ENTRYPOINT [ "/bin/bash" ]
