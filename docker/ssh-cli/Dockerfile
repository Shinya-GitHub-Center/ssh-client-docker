FROM python:3.9.14
ARG USERNAME=ssh-client
ARG GROUPNAME=ssh-client
ARG UID=1000
ARG GID=1000
RUN groupadd -g $GID $GROUPNAME && \
    useradd -m -s /bin/bash -u $UID -g $GID $USERNAME
WORKDIR /home/ssh-client/workdir
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y vim less tree jq
