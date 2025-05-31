FROM debian:stable

RUN apt-get update

# Install 64-bit development tools and libraries
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y \
    apt-utils \
    gcc-multilib \
    g++-multilib \
    libc6 \
    libstdc++6 \
    make \
    build-essential \
    pkg-config \
    git \
    wget \
    vim \
    libc6 \
    libfreetype6 \
    libsm6 \
    libxrender1 \
    libfontconfig1 \
    libxext6 \
    libxtst6 \
    lib32z1 \
    expect \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

ADD ./libpng /libpng-installer
RUN cd /libpng-installer && \
    DEBIAN_FRONTEND=noninteractive apt install -y ./libpng12-0_1.2.54-6_amd64.deb 
    
ADD fpga /usr/local/sbin/fpga
ENTRYPOINT ["/usr/local/sbin/fpga"]
LABEL com.halfmanhalftaco.fpga.base="debian:stable"