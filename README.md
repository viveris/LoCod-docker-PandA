# locod-panda-docker : Docker with Panda-Bambu framework

## Description

This repository contains a Dockerfile to make a Docker image with the followings components :

- **Panda-Bambu** : a free framework aimed at assisting the designer during the high-level synthesis of complex applications, supporting most of the C constructs (e.g., function calls and sharing of the modules, pointer arithmetic and dynamic resolution of memory accesses, accesses to array and structs, parameter passing either by reference or copy, …). Bambu is developed for Linux systems, it is written in C++11, and it can be freely downloaded under GPL license. <br>
Here is the Panda-Bambu website : https://panda.deib.polimi.it/

In the context of the Locod project, this tool is used to convert the C code function in RTL components that we can next integrate into the FPGA design.

<br>

## Dependencies

Here are the dependencies installed within the Dockerfile to make this tool working :

`autoconf autoconf-archive automake libtool g++ gcc-4.8 g++-4.8 gcc-5 g++-5 gcc-6 g++-6 gcc-7 g++-7 gcc-8 g++-8 gcc-4.8-plugin-dev gcc-5-plugin-dev gcc-6-plugin-dev gcc-7-plugin-dev  gcc-8-plugin-dev gcc-4.8-multilib gcc-5-multilib gcc-6-multilib gcc-7-multilib gcc-8-multilib g++-4.8-multilib g++-5-multilib g++-6-multilib g++-7-multilib g++-8-multilib gfortran-4.8 gfortran-4.8-multilib gfortran-5 gfortran-5-multilib gfortran-6 gfortran-6-multilib gfortran-7 gfortran-7-multilib gfortran-8 gfortran-8-multilib clang-4.0 libclang-4.0-dev libclang-6.0-dev clang-6.0 libclang-6.0-dev clang-7 libclang-7-dev clang-8 libclang-8-dev clang-9 libclang-9-dev libbdd-dev libboost-all-dev libmpc-dev libmpfr-dev libxml2-dev liblzma-dev libmpfi-dev zlib1g-dev libicu-dev bison doxygen flex graphviz iverilog verilator make libsuitesparse-dev libglpk-dev git ca-certificates`

<br>

## Run command and usage

Once built, the Docker image can be used to create a container with the following command:

```console
docker run -it --rm -v ... DOCKER_IMAGE_NAME
```

In the docker, the Panda-Bambu tool can be launched with the command :
```console
bambu ... [C file]
```
