# https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/docker?view=azure-devops

FROM ubuntu:18.04

# To make it easier for build and release pipelines to run apt-get,
# configure apt to not require confirmation (assume the -y argument by default)
ENV DEBIAN_FRONTEND=noninteractive
RUN echo "APT::Get::Assume-Yes \"true\";" > /etc/apt/apt.conf.d/90assumeyes

RUN wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb \
    && dpkg -i packages-microsoft-prod.deb

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    jq \
    git \
    iputils-ping \
    libcurl3 \
    libicu55 \
    libunwind8 \
    wget \
    netcat \
    unzip \
    build-essential \
    ssh \
    mono-complete \
    software-properties-common \
    apt-transport-https \
    powershell \
    moby-engine \
    moby-cli

# Update packages
RUN apt-get upgrade -y

# Update azure-cli
RUN curl -sL https://aka.ms/InstallAzureCLIDeb | bash

# Cleanup
RUN apt-get autoremove -y \
    && apt-get autoclean -y\
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /etc/apt/sources.list.d/*

WORKDIR /azp

COPY ./start.sh .
RUN chmod +x start.sh

CMD ["./start.sh"]