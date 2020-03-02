# Adds customized Valgrind tools to an Ubuntu base image
# This is intended to add to similar existing docker images by just changing
# the FROM line.

FROM ubuntu:14.04
MAINTAINER Deby Katz

RUN echo "deb http://us.archive.ubuntu.com/ubuntu/ trusty universe" >> /etc/apt/sources.list
RUN apt-get -y update
RUN apt-get --no-install-recommends install -y automake make autoconf git g++ libc6-dbg \
    && apt-get clean \
    && rm -rf \
        /var/lib/apt/lists/* \
        /tmp/* \
        /var/tmp/* \
        /usr/share/man \
        /usr/share/doc \
        /usr/share/doc-base

RUN cd $HOME; git clone https://github.com/osssp/valgrind-tools.git
RUN cd $HOME/valgrind-tools ; ./autogen.sh ; ./configure --prefix=$HOME/valgrind-bin; make install
