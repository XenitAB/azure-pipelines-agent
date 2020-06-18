# https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/docker?view=azure-devops

FROM ubuntu:18.04

# To make it easier for build and release pipelines to run apt-get,
# configure apt to not require confirmation (assume the -y argument by default)
ENV DEBIAN_FRONTEND=noninteractive
RUN echo "APT::Get::Assume-Yes \"true\";" > /etc/apt/apt.conf.d/90assumeyes

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    jq \
    git \
    iputils-ping \
    libcurl4 \
    libicu60 \
    libunwind8 \
    wget \
    netcat \
    unzip \
    build-essential \
    openssh-client \
    mono-complete \
    software-properties-common \
    apt-transport-https \
    python3 \
    python3-setuptools \
    python3-pip

# Update packages
RUN apt-get upgrade -y

# Update azure-cli
RUN curl -sL https://aka.ms/InstallAzureCLIDeb | bash

# Update powershell
RUN wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb \
    && dpkg -i packages-microsoft-prod.deb \
    && apt-get update \
    && apt-get install -y powershell moby-engine moby-cli

# Cleanup
RUN apt-get autoremove -y \
    && apt-get autoclean -y\
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /etc/apt/sources.list.d/*

WORKDIR /azp

COPY ./start.sh .
RUN chmod +x start.sh

CMD ["./start.sh"]