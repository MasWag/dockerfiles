FROM ocaml/opam

MAINTAINER Masaki Waga "masakiwaga@gmail.com"
RUN sudo apt-get update
RUN sudo apt-get install zlib1g-dev libgmp-dev libgtksourceview2.0-dev libgnomecanvas2-dev autoconf -y
RUN opam update
RUN opam install frama-c coq why3 alt-ergo -y

