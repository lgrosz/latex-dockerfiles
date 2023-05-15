FROM ubuntu:22.04 as base

ARG DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y \
  perl-modules \
  wget \
  && apt clean && rm -rf /var/lib/apt/lists/*

RUN \
  wget https://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz && \
  zcat < install-tl-unx.tar.gz | tar xf - && \
  rm install-tl-unx.tar.gz && \
  cd install-tl-* && \
  ./install-tl --no-interaction

ENV PATH="${PATH}:/usr/local/texlive/2023/bin/x86_64-linux"

RUN tlmgr install \
    l3build
  

FROM base as test
RUN l3build

