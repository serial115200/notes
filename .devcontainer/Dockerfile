# syntax=docker/dockerfile:1.3-labs

ARG VARIANT=3-bullseye
FROM mcr.microsoft.com/vscode/devcontainers/python:${VARIANT}

RUN <<EOF
#sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list.d/debian.sources
sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list
python3 -m pip config set global.index-url https://mirrors.ustc.edu.cn/pypi/web/simple
EOF

RUN <<EOF
apt-get update
apt-get install --no-install-recommends --yes \
     graphviz \
     imagemagick \
     make \
     git
apt-get autoremove
apt-get clean
rm -rf /var/lib/apt/lists/*
EOF

RUN <<EOF
python3 -m pip install --no-cache-dir --upgrade pip
python3 -m pip install --no-cache-dir \
     Sphinx==7.1.2 \
     Pillow \
     esbonio \
     docutils
EOF
