FROM mcr.microsoft.com/devcontainers/base:focal

ENV USERNAME vscode

RUN sed -i 's@//.*archive.ubuntu.com@//mirrors.ustc.edu.cn@g' /etc/apt/sources.list

RUN DEBIAN_FRONTEND=noninteractive apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y apt-transport-https curl
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y \
    cmake python python3-pip zlib1g-dev git

RUN curl -fsSL https://apt.llvm.org/llvm.sh -o /tmp/llvm.sh && chmod +x /tmp/llvm.sh && /tmp/llvm.sh 12 all

# manually install features so that we can use proxy
RUN git clone https://github.com/devcontainers/features.git /tmp/features
RUN UID="1000" GID="1000" bash /tmp/features/src/common-utils/install.sh
RUN VERSION="os-provided" bash /tmp/features/src/git/install.sh
RUN VERSION="lts" bash /tmp/features/src/node/install.sh
