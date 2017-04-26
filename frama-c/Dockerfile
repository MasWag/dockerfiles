FROM base/archlinux

MAINTAINER Masaki Waga "masakiwaga@gmail.com"
RUN pacman -Sy archlinux-keyring --noconfirm
RUN pacman -Syu --needed base-devel --noconfirm
RUN cd /tmp/ && curl -L -O https://aur.archlinux.org/cgit/aur.git/snapshot/frama-c.tar.gz && tar zxvf frma-c.tar.gz
RUN cd /tmp/frama-c/ && makepkg -sri --asroot --noconfirm

