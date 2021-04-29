FROM mikefarah/yq:4
FROM alpine/git:latest

COPY --from=0 /usr/bin/yq /usr/bin/

RUN apk update &&\
    apk add --no-cache gettext

ENV WORKDIR=/workdir

RUN adduser -D -h $WORKDIR -u 1001 git

WORKDIR $WORKDIR

RUN rm -rf ..?* .[!.]* *

USER git

ENTRYPOINT [ "/bin/sh" ]
