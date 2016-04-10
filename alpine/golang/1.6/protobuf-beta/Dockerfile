############################################################
# Dockerfile to build protobuf3 enabled container images
# Based on Alpine
############################################################

FROM golang:1.6-alpine

MAINTAINER Olivier Boucher <info@olivierboucher.com>

# Install required utilities
RUN apk update && apk add curl unzip

# Install protoc beta from pre-compiled source
RUN cd /tmp && curl -LOk https://github.com/google/protobuf/releases/download/v3.0.0-beta-2/protoc-3.0.0-beta-2-linux-x86_64.zip
RUN cd /tmp && unzip protoc-3.0.0-beta-2-linux-x86_64.zip
RUN cd /tmp && cp protoc /usr/local/bin/protoc

# Set working directory back to home since the golang images sets it to $GOPATH
WORKDIR ~/
