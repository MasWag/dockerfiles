FROM ocaml/opam:debian-10_ocaml-4.04.0

MAINTAINER Masaki Waga "masakiwaga@gmail.com"
RUN sudo apt-get update
RUN sudo apt-get install zlib1g-dev libgmp-dev libgtksourceview2.0-dev libgnomecanvas2-dev autoconf clang-3.9 libclang-3.9-dev -y
RUN opam update
RUN opam install frama-c coq why3 alt-ergo -y


RUN curl https://frama-c.com/downloads/frama-clang-0.0.6.tar.gz -o frama-clang-0.0.6.tar.gz
RUN tar xzvf frama-clang-0.0.6.tar.gz
RUN opam switch 4.04.0
RUN opam install camlp4
RUN eval `opam config env` && cd frama-clang-0.0.6 && ./configure && make && sudo make install
