FROM ubuntu:14.04
MAINTAINER Daeyun Shin <dshin11@illinois.edu>

ENV DEBIAN_FRONTEND noninteractive

ENV CUDA_RUN http://developer.download.nvidia.com/compute/cuda/7.5/Prod/local_installers/cuda_7.5.18_linux.run

RUN apt-get update && apt-get install -q -y \
  build-essential \
  wget

RUN cd /opt && \
  wget $CUDA_RUN

RUN cd /opt && \
  mkdir nvidia_installers && \
  sh ./cuda* -extract=`pwd`/nvidia_installers

RUN cd /opt/nvidia_installers && \
# Silent, no-network, no-kernel-module
  ./NVIDIA-Linux*.run -s -N --no-kernel-module

RUN cd /opt/nvidia_installers && \
  ./cuda-linux64*.run -noprompt && \
# Prints out version info
  ls -lah

ENV LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH PATH=/usr/local/cuda/bin:$PATH
