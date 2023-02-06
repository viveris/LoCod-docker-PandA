FROM bambuhls/appimage:bionic

LABEL maintainer="Hugo KIEFFER <hugo.kieffer@viveris.fr>"
LABEL description="PandA docker"

# Version of PandA tools to install
ARG PANDA_VERSION=v0.9.8

# Additional dependencies
RUN apt install -y --no-install-recommends  git ca-certificates

# PandA build and install
RUN git clone -b ${PANDA_VERSION} https://github.com/ferrandi/PandA-bambu /home/panda/bambu

RUN cd /home/panda/bambu && \ 
    bash ./.devcontainer/library-scripts/compiler-download.sh / gcc-4.9,gcc-7,clang-6,clang-12 && \
    bash ./.devcontainer/library-scripts/compiler-setup.sh
 
RUN cd /home/panda/bambu && \
    make -f Makefile.init && \
    mkdir obj && \
    cd obj && \
    ../configure --prefix=/opt/panda --enable-flopoco --enable-opt --enable-release && \
    make && \
    make install && \
    rm -rf /home/panda/bambu

RUN apt clean

RUN useradd -s /bin/bash -m locod

USER locod

ENV PATH=$PATH:/opt/panda/bin
