# Dockerfile to build an image with the local version of psiphon-tunnel-core.
#
# See README.md for usage instructions.

FROM ubuntu:20.04

# Install system-level dependencies.
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update -y && apt-get install -y --no-install-recommends \
    build-essential \
    ca-certificates \
    curl \
    gcc-mingw-w64-i686 \
    gcc-mingw-w64-x86-64 \
    gcc-multilib \
    git \
    mingw-w64 \
    mercurial \
    pkg-config \
    upx \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

# Install Go.
<<<<<<< HEAD
ENV GOVERSION=go1.17 GOROOT=$HOME/go GOPATH=$HOME/go PATH=$PATH:/usr/bin/go/bin:/go/bin CGO_ENABLED=1
=======
ENV GOVERSION=go1.17.2 GOROOT=/usr/local/go GOPATH=/go PATH=$PATH:/usr/local/go/bin:/go/bin CGO_ENABLED=1
>>>>>>> upstream/master

RUN curl -L https://storage.googleapis.com/golang/$GOVERSION.linux-amd64.tar.gz -o /tmp/go.tar.gz \
   && tar -C /usr/bin -xzf /tmp/go.tar.gz \
   && rm /tmp/go.tar.gz \
   && echo $GOVERSION > $GOROOT/VERSION

# Get external Go dependencies.
RUN go get github.com/pwaller/goupx

WORKDIR $GOPATH/src/github.com/Psiphon-Labs/psiphon-tunnel-core/ConsoleClient
