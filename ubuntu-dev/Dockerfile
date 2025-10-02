FROM ubuntu:25.04

RUN apt update -y && \
    apt upgrade -y && \
    apt install -y wget software-properties-common gnupg lsb-release \
        curl tar git zip unzip make autoconf libtool ninja-build cmake && \
    wget https://apt.llvm.org/llvm.sh && \
    chmod +x llvm.sh && \
    ./llvm.sh 22 && \
    apt update -y && \
    apt install -y clang-22 clang-tidy-22 clang-format-22 g++-15 && \
    update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-15 10 && \
    update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-15 10 && \
    update-alternatives --install /usr/bin/clang clang /usr/bin/clang-22 200 && \
    update-alternatives --install /usr/bin/clang++ clang++ /usr/bin/clang++-22 200 && \
    update-alternatives --install /usr/bin/clang-tidy clang-tidy /usr/bin/clang-tidy-22 200 && \
    update-alternatives --install /usr/bin/clang-format clang-format /usr/bin/clang-format-22 200 && \
    update-alternatives --install /usr/bin/run-clang-tidy run-clang-tidy /usr/bin/run-clang-tidy-22 200

# raylib dependencies
RUN apt install -y libxinerama-dev libxcursor-dev xorg-dev libglu1-mesa-dev pkg-config \
    libgl1-mesa-dev libx11-dev libxrandr-dev
