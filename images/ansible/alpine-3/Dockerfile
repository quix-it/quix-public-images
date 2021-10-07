FROM alpine:3.13

RUN apk update && \
    apk add openssh-client ansible ansible-lint jq python3 py3-pip py3-jmespath
RUN ansible-galaxy collection install community.docker community.general community.crypto ansible.posix
RUN pip3 install yq

RUN apk add bash rsync

WORKDIR /workdir

ENV PS1='\u@\h:\w\$ '

ENTRYPOINT ["/bin/bash"]
