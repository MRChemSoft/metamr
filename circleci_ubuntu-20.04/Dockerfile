FROM ubuntu:20.04

# Set an encoding to make things work smoothly.
ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8

# Add a timestamp for the build. Also, bust the cache.
ADD http://worldtimeapi.org/api/ip /opt/docker/etc/timestamp

ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get --yes -qq update \
 && apt-get --yes -qq upgrade \
 && apt-get --yes -qq install \
                      bzip2 \
		      cmake \
                      cpio \
                      curl \
                      g++ \
                      gcc \
                      git \
                      libeigen3-dev \
                      libidn11-dev \
                      libopenmpi-dev \
                      openmpi-bin \
                      python3 \
		      python-is-python3 \
 && rm -rf /var/lib/apt/lists/*

# Run common commands
COPY run_commands /opt/docker/bin/run_commands
RUN /opt/docker/bin/run_commands

ENV PATH $PATH:/root/.local/bin

ENV LD_LIBRARY_PATH /root/.local/lib${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}

SHELL ["/bin/bash"]
