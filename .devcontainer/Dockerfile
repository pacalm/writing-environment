FROM ubuntu:24.04

RUN mkdir -p /home/ubuntu/workdir

WORKDIR /home/ubuntu/workdir

RUN apt update && apt install -y \
    curl \
    git \
    wget \
    xz-utils \
    && apt -y clean && rm -rf /var/lib/apt/lists/*

RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash \
    && . ~/.bashrc \
    && nvm install 22 \
    && npm install \
        textlint \
        textlint-rule-preset-ja-technical-writing \
        --save-dev

RUN wget https://github.com/jgm/pandoc/releases/download/3.6.2/pandoc-3.6.2-1-amd64.deb \
    && apt install ./pandoc-3.6.2-1-amd64.deb \
    && wget https://github.com/lierdakil/pandoc-crossref/releases/download/v0.3.18.1a/pandoc-crossref-Linux-X64.tar.xz \
    && tar -xf pandoc-crossref-Linux-X64.tar.xz \
    && mv pandoc-crossref /usr/local/bin