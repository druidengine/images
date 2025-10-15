FROM ubuntu:25.04

RUN apt update -y && \
    apt upgrade -y && \
    apt install -y wget software-properties-common gnupg lsb-release mono-complete \
        curl tar git zip unzip make autoconf libtool ninja-build cmake

# Install gcc 15.2
RUN apt install -y build-essential flex bison libgmp-dev libmpc-dev libmpfr-dev texinfo libisl-dev && \
    wget https://ftp.gnu.org/gnu/gcc/gcc-15.2.0/gcc-15.2.0.tar.xz && \
    tar -xf gcc-15.2.0.tar.xz && \
    cd gcc-15.2.0 && \
    mkdir build && \
    cd build && \
    ../configure --prefix=/usr/local/gcc-15.2 --enable-languages=c,c++ --disable-multilib && \
    make -j $(nproc --all) && \
    make install && \
    update-alternatives --install /usr/bin/gcc gcc /usr/local/gcc-15.2/bin/gcc 152 && \
    update-alternatives --install /usr/bin/g++ g++ /usr/local/gcc-15.2/bin/g++ 152

# Install clang-22
RUN wget https://apt.llvm.org/llvm.sh && \
    chmod +x llvm.sh && \
    ./llvm.sh 22 && \
    apt update -y && \
    apt install -y clang-22 clang-tidy-22 clang-format-22 && \
    update-alternatives --install /usr/bin/clang clang /usr/bin/clang-22 200 && \
    update-alternatives --install /usr/bin/clang++ clang++ /usr/bin/clang++-22 200 && \
    update-alternatives --install /usr/bin/clang-tidy clang-tidy /usr/bin/clang-tidy-22 200 && \
    update-alternatives --install /usr/bin/clang-format clang-format /usr/bin/clang-format-22 200 && \
    update-alternatives --install /usr/bin/run-clang-tidy run-clang-tidy /usr/bin/run-clang-tidy-22 200

# Install Raylib dependencies
RUN apt install -y libxinerama-dev libxcursor-dev xorg-dev libglu1-mesa-dev pkg-config libgl1-mesa-dev libx11-dev libxrandr-dev
