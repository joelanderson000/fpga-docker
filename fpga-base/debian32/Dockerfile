FROM debian:stable
# Enable 32-bit architecture and update package lists
RUN dpkg --add-architecture i386 && \
    apt-get update

# Install 32-bit development tools and libraries
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y \
    apt-utils \
    gcc-multilib \
    g++-multilib \
    libc6:i386 \
    libstdc++6:i386 \
    make \
    build-essential \
    pkg-config \
    git \
    wget \
    vim \
    libc6:i386 \
    libfreetype6:i386 \
    libsm6:i386 \
    libxrender1:i386 \
    libfontconfig1:i386 \
    libxext6:i386 \
    libxtst6:i386 \
    lib32z1 \
    expect \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

ADD ./libpng /libpng-installer
RUN cd /libpng-installer && \
    DEBIAN_FRONTEND=noninteractive apt install -y ./libpng12-0_1.2.54-6_i386.deb
    
ADD fpga /usr/local/sbin/fpga
ENTRYPOINT ["/usr/local/sbin/fpga"]
LABEL com.anderson.image.base="debian32:stable"