# From Daniel Quinn repo : https://gitlab.com/danielquinn/megacmd-alpine/-/tree/master

FROM alpine

RUN echo "http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories
RUN echo "http://dl-cdn.alpinelinux.org/alpine/v3.9/main" >> /etc/apk/repositories

RUN apk add --update --no-cache \
  c-ares \
  crypto++ \
  libcurl \
  libtool \
  libuv \
  pcre \
  pcre-dev \
  readline \
  sqlite \
  sqlite-dev \
  zlib
RUN apk add --no-cache \
  autoconf \
  automake \
  c-ares-dev \
  crypto++-dev \
  curl \
  curl-dev \
  cvs \
  file \
  g++ \
  gcc \
  git \
  libc-dev \
  libffi-dev \
  libressl2.7-libcrypto \
  libressl-dev \
  libsodium \
  libsodium-dev \
  libuv-dev \
  make \
  openssl \
  openssl-dev \
  readline-dev \
  zlib-dev \
  \
  && cd /opt \
  && cvs -z3 -d:pserver:anonymous@freeimage.cvs.sourceforge.net:/cvsroot/freeimage co -P FreeImage \
  && cd FreeImage \
  && make -j $(nproc) \
  && make install \
  \
  && git clone https://github.com/meganz/MEGAcmd.git /opt/MEGAcmd \
  && cd /opt/MEGAcmd \
  && git submodule update --init --recursive \
  && sh autogen.sh \
  && ./configure \
  && make -j $(nproc) \
  && make install \
  \
  && cd /opt/FreeImage \
  && make clean \
  && cd / \
  && rm -rf /opt/FreeImage
