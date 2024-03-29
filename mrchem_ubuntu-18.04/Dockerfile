FROM ubuntu:18.04

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
                      cpio \
                      curl \
                      emacs-nox \
                      g++ \
                      gcc \
                      git \
                      gosu \
                      libblas-dev \
                      libboost-all-dev \
                      libeigen3-dev \
                      libidn11-dev \
                      liblapack-dev \
                      libopenmpi-dev \
                      libpython3-all-dev \
                      openmpi-bin \
                      python3-dev \
                      python3-pip \
                      sudo \
                      vim-nox \
 && apt-get --yes -qq clean \
 && rm -rf /var/lib/apt/lists/*

# Run common commands
COPY run_commands /opt/docker/bin/run_commands
RUN /opt/docker/bin/run_commands

# Add a file for users to source
COPY entrypoint_source /opt/docker/bin/entrypoint_source

# Add a file that wraps that for use with the `ENTRYPOINT`.
COPY entrypoint /opt/docker/bin/entrypoint

# Ensure that all containers start with tini and the user selected process.
ENTRYPOINT [ "/opt/docker/bin/tini", "--", "/opt/docker/bin/entrypoint" ]

# Provide a default command (`bash`), which will start if the user doesn't specify one.
CMD [ "/bin/bash" ]
