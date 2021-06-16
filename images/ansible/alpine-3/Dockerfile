FROM alpine:3.13

RUN apk update && \
    apk add openssh-client ansible ansible-lint jq python3 py3-pip
RUN ansible-galaxy collection install community.docker community.general community.crypto
RUN pip3 install yq

RUN adduser -D -h /home/ansible -u 1001 ansible

USER ansible

WORKDIR /src

ENTRYPOINT ["/bin/sh"]
