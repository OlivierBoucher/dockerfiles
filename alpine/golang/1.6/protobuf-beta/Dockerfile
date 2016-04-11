############################################################
# Dockerfile to build protobuf3 enabled container images
# Based on Alpine
############################################################

FROM golang:1.6-alpine

MAINTAINER Olivier Boucher <info@olivierboucher.com>

# Install required utilities
RUN apk update && apk add curl unzip make git libtool automake autoconf g++

# Get and compile protoc beta
RUN cd /tmp && \
    git clone https://github.com/google/protobuf.git && \
    cd protobuf && \
    git checkout v3.0.0-beta-2 && \
    ./autogen.sh && \
    ./configure && \
    make && \
    make check && \
    make install

RUN rm -rf /tmp/protobuf

# Set working directory back to home since the golang images sets it to $GOPATH
WORKDIR ~/

# Override entrypoint to use bash
ENTRYPOINT ["/bin/sh", "-c"]
