# Use Debian Bullseye slim as the base image
FROM debian:bullseye-slim

# Set the maintainer label
LABEL maintainer="masakiwaga@gmail.com"

# Update and install necessary packages
RUN apt-get update && apt-get install -y \
    gnupg \
    ca-certificates \
    wget \
    cmake build-essential gdb ninja-build pkg-config\
    && rm -rf /var/lib/apt/lists/*

# Add Spot's repository and key
RUN echo 'deb http://www.lrde.epita.fr/repo/debian/ stable/' >> /etc/apt/sources.list \
    && wget -O- https://www.lrde.epita.fr/repo/debian.gpg | gpg --dearmor > /etc/apt/trusted.gpg.d/spot-archive-keyring.gpg \
    && apt-get update

# Install Spot
RUN apt-get install -y spot libspot-dev \
    && rm -rf /var/lib/apt/lists/*

# Default command or entry point
CMD ["/bin/bash"]
