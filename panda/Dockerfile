FROM ubuntu:bionic
MAINTAINER Julien ARMENGAUD <julien.armengaud@viveris.fr>
LABEL description="Docker with Panda-Bambu framework"


# Version of PandA tools to install
ARG PANDA_VERSION=v0.9.8


# Reset workdir
WORKDIR /


# Install requiered packages
RUN	apt update && \
	apt install --yes autoconf autoconf-archive automake libtool g++ gcc-4.8 g++-4.8 gcc-5 g++-5 gcc-6 g++-6 gcc-7 g++-7 gcc-8 g++-8 gcc-4.8-plugin-dev gcc-5-plugin-dev gcc-6-plugin-dev gcc-7-plugin-dev  gcc-8-plugin-dev gcc-4.8-multilib gcc-5-multilib gcc-6-multilib gcc-7-multilib gcc-8-multilib g++-4.8-multilib g++-5-multilib g++-6-multilib g++-7-multilib g++-8-multilib gfortran-4.8 gfortran-4.8-multilib gfortran-5 gfortran-5-multilib gfortran-6 gfortran-6-multilib gfortran-7 gfortran-7-multilib gfortran-8 gfortran-8-multilib clang-4.0 libclang-4.0-dev libclang-6.0-dev clang-6.0 libclang-6.0-dev clang-7 libclang-7-dev clang-8 libclang-8-dev clang-9 libclang-9-dev libbdd-dev libboost-all-dev libmpc-dev libmpfr-dev libxml2-dev liblzma-dev libmpfi-dev zlib1g-dev libicu-dev bison doxygen flex graphviz iverilog verilator make libsuitesparse-dev libglpk-dev git ca-certificates && \
	apt clean


# PandA build and install
RUN git clone -b ${PANDA_VERSION} https://github.com/ferrandi/PandA-bambu.git /tmp/panda-bambu
RUN cd /tmp/panda-bambu && \
    make -f Makefile.init && \
    mkdir obj && \
    cd obj && \
    ../configure --prefix=/opt/panda --enable-flopoco --enable-opt --enable-release && \
    make && \
    make install && \
    rm -rf /tmp/panda-bambu


# Adding Panda-Bambu directory to PATH
ENV PATH=/opt/panda/bin:$PATH


# Change workdir
RUN mkdir /workdir
RUN chmod -R 777 /workdir
WORKDIR /workdir
