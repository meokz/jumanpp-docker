FROM debian:buster-slim

ARG JPP_VERSION=2.0.0-rc3
ARG JPP_PATH=/usr/local
ENV PATH=${JPP_PATH}/bin:$PATH

RUN mkdir -p /mytmp \
    && cd /mytmp \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
    curl \
    g++ \
    make \
    cmake \
    xz-utils \
    && curl -OL --insecure https://github.com/ku-nlp/jumanpp/releases/download/v${JPP_VERSION}/jumanpp-${JPP_VERSION}.tar.xz \
    && tar xf jumanpp-${JPP_VERSION}.tar.xz \
    && cd jumanpp-${JPP_VERSION}/ \
    && mkdir bld \
    && cd bld \
    && cmake .. \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=${JPP_PATH} \
    && make -j "$(nproc)" \
    && make install \
    && cd / \
    && rm -rf /mytmp \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
