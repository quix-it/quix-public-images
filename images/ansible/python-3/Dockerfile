FROM python:3-alpine

RUN apk update && apk add --no-cache openssh bash linux-headers libffi libffi-dev make gcc g++ musl-dev openssl openssl-dev rsync
RUN pip install "ansible<2.11,>=2.10" yq jmespath

RUN ansible-galaxy collection install community.docker community.general community.crypto ansible.posix

WORKDIR /workdir

ENV PS1='\u@\h:\w\$ '

ENTRYPOINT ["/bin/bash"]