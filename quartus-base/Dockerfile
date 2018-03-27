FROM ubuntu:16.04

# install required dependencies
RUN apt-get update && \
    apt-get -y install \
        ca-certificates \
        lib32ncurses5-dev \
        libcrypto++9v5 \
        libfontconfig1 \
        libglib2.0-0 \
        libsm6 \
        libssl-dev \
        libxrender1 \
        libzmq3-dev \
        git \
        locales \
        make \
        expect \
        libtcmalloc-minimal4 \
        wget \
        build-essential \
        lsb libncurses-dev \
        lib32stdc++6 \
        lib32z1 lib32ncurses5

# Create a non-root user for builds
RUN adduser --disabled-password --gecos '' builder && \
    usermod builder -aG staff

# Set the locale, Quartus expects en_US.UTF-8
RUN echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen

ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

USER builder
