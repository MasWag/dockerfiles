FROM ubuntu:jammy
MAINTAINER "Masaki Waga" <masakiwaga@gmail.com>
ENV container docker
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y build-essential cmake git

# Build hexl
RUN git clone https://github.com/intel/hexl.git
RUN cmake -S ./hexl -B hexl/build && cmake --build hexl/build && cmake --install hexl/build

# Build SEAL
RUN git clone https://github.com/microsoft/SEAL.git -b v4.1.1
RUN cmake -S ./SEAL -B SEAL/build && cmake --build SEAL/build && cmake --install SEAL/build
RUN ln /usr/local/lib/libseal-4.1.a /usr/local/lib/libseal.a
