FROM archlinux/base
MAINTAINER "Masaki Waga" <masakiwaga@gmail.com>
ENV container docker

# Install depending packages
RUN pacman -Sy --needed base-devel make cmake bison flex eigen boost doxygen git --noconfirm

# Download the MONAA source
RUN git clone https://github.com/MasWag/monaa.git

# Build MONAA
RUN mkdir -p monaa/build
RUN cd monaa/build && cmake -DCMAKE_BUILD_TYPE=Release .. && make monaa && make install