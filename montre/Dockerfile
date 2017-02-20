FROM maswag/pure-lang
MAINTAINER "Masaki Waga" <masakiwaga@gmail.com>
ENV container docker

RUN pacman -S git --noconfirm

RUN git clone https://github.com/doganulus/montre
RUN make -C montre && make install -C montre