FROM mikefarah/yq:4
FROM alpine/git:latest

COPY --from=0 /usr/bin/yq /usr/bin/

RUN apk update &&\
    apk add --no-cache gettext jq curl grep bash

ENV WORKDIR=/workdir

WORKDIR $WORKDIR

RUN rm -rf ..?* .[!.]* *

ENTRYPOINT [ "/bin/bash" ]
