FROM ubuntu:25.04

# Update package list and install g++-15
RUN apt-get update && \
    apt-get install -y g++-15 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Set g++-15 as the default g++
RUN update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-15 100 && \
    update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-15 100

# Verify installation
RUN g++ --version
