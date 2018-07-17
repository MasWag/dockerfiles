FROM base/archlinux

MAINTAINER Masaki Waga "masakiwaga@gmail.com"
RUN pacman -Sy gcc cmake make libedit  --noconfirm
RUN cd /tmp/ && curl -L -O https://divine.fi.muni.cz/download/divine-4.1.10.tar.gz && tar zxvf divine-4.1.10.tar.gz
RUN cd /tmp/divine-4.1.10 && make && make install

