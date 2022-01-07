FROM mikefarah/yq:4
FROM gcr.io/google.com/cloudsdktool/cloud-sdk:alpine

COPY --from=0 /usr/bin/yq /usr/bin/

RUN apk update &&\
    apk add --no-cache gettext jq curl grep gettext ca-certificates bash bash-completion moreutils

SHELL ["/bin/bash", "-c"]

RUN source /google-cloud-sdk/completion.bash.inc && \
    source /google-cloud-sdk/path.bash.inc && \
    echo "source /google-cloud-sdk/completion.bash.inc" >> ~/.bashrc && \
    echo "source /google-cloud-sdk/path.bash.inc" >> ~/.bashrc

RUN gcloud components install -q kubectl && \
    kubectl completion bash >/google-cloud-sdk/kubectl.bash.inc && \
    echo "source /google-cloud-sdk/kubectl.bash.inc" >> ~/.bashrc

ENV WORKDIR=/workdir
WORKDIR $WORKDIR

ENV PS1='\u@\h:\w\$ '

ENTRYPOINT [ "/google-cloud-sdk/bin/gcloud" ]
