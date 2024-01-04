ARG base
FROM ${base}
LABEL description="randomgraphics common build environment for Ubuntu 22.04"
ARG DEBIAN_FRONTEND=noninteractive

# Install common build dependencies on Ubuntu
RUN apt-get update && apt-get install -y --no-install-recommends \
    wget \
    build-essential \
    cmake \
    git \
    git-lfs \
    openssh-client \
    ninja-build \
    vim \
    python3 \
    python3-pip \
    binutils-dev \
    clang-14 \
    clang-15 \
    clang-format-12 \
    clang-format-14 \
    libx11-xcb-dev \
    libxkbcommon-dev \
    libwayland-dev \
    libxrandr-dev \
    libegl1-mesa-dev \
    libglfw3-dev \
    libxinerama-dev \
    libxcursor-dev \
    libxi-dev \
    libdw-dev \
    libunwind-dev \
    libdwarf-dev \
    && rm -rf /var/lib/apt/lists/*

# Install pyhton packages
RUN pip3 install termcolor
