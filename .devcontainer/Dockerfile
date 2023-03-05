FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y --no-install-recommends \
    ca-certificates \
    curl \
    file \
    build-essential \
    cmake \
    gdb \
    git \
    make \
    sudo \
    pkg-config \
    autoconf \
    automake \
    lsb-release \
    wget \
    software-properties-common 


RUN apt update && \
    apt install -y \
    libzmq3-dev \
    libboost-dev


ARG USERNAME=user
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Create a non-root user
RUN groupadd --gid $USER_GID $USERNAME \
  && useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME \
  # [Optional] Add sudo support for the non-root user
  && apt-get update \
  && apt-get install -y sudo git-core bash-completion \
  && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME\
  && chmod 0440 /etc/sudoers.d/$USERNAME \
  # Cleanup
  && rm -rf /var/lib/apt/lists/* 

USER $USERNAME
WORKDIR /home/$USERNAME

RUN mkdir -p ~/git \
  && cd ~/git \
  && git clone https://github.com/BehaviorTree/BehaviorTree.CPP \
  && mkdir BehaviorTree.CPP/build \
  && cd BehaviorTree.CPP/build \
  && cmake .. \
  && make

USER root
RUN cd /home/$USERNAME/git/BehaviorTree.CPP/build \
  && make install

