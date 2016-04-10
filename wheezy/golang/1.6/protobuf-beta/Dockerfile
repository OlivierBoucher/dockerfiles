############################################################
# Dockerfile to build protobuf3 enabled container images
# Based on Wheezy
############################################################

FROM golang:1.6-wheezy

MAINTAINER Olivier Boucher <info@olivierboucher.com>

# Install required utilities
RUN apt-get update && apt-get install -y curl unzip make git

# Install protoc beta from pre-compiled source
RUN cd /tmp && \
    curl -LOk https://github.com/google/protobuf/releases/download/v3.0.0-beta-2/protoc-3.0.0-beta-2-linux-x86_64.zip && \
    unzip protoc-3.0.0-beta-2-linux-x86_64.zip && \
    cp protoc /usr/local/bin/protoc

# Set working directory back to home since the golang images sets it to $GOPATH
WORKDIR ~/

# Override entrypoint to use bash
ENTRYPOINT ["/bin/bash", "-c"]
