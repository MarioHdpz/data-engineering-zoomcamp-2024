FROM mcr.microsoft.com/devcontainers/base:ubuntu

ARG USERNAME=vscode

# Everything runs as root during build time, so we want
# to make sure the vscode user can edit these paths too:
RUN chmod 777 -R /home/${USERNAME}/.config

# Set container timezone:
ARG TZ="UTC"
RUN ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime

# Required for Python - Confluent Kafka on M1 Silicon
RUN apt update && apt -y install software-properties-common gcc
RUN git clone https://github.com/edenhill/librdkafka
RUN cd librdkafka && ./configure && make && make install && ldconfig
