FROM archlinux/archlinux
MAINTAINER "Masaki Waga" <masakiwaga@gmail.com>
ENV container docker

RUN pacman -Sy archlinux-keyring  --noconfirm
RUN pacman -Syu --ignore ca-certificates --noconfirm
RUN pacman-db-upgrade
RUN pacman -S --force ca-certificates --noconfirm
RUN trust extract-compat
RUN pacman -S --force firefox --noconfirm
 
ENV HOME /root
CMD /usr/bin/firefox
