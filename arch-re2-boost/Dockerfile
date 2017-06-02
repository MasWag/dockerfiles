FROM base/archlinux
MAINTAINER "Masaki Waga" <masakiwaga@gmail.com>
ENV container docker

# Update building environment
RUN pacman -Sy archlinux-keyring  --noconfirm
RUN pacman -Suw --noconfirm
RUN rm /etc/ssl/certs/ca-certificates.crt 
RUN pacman -Su --noconfirm
RUN pacman-db-upgrade
RUN trust extract-compat
RUN pacman -S --needed base-devel --noconfirm

# Install depending packages
RUN pacman -S re2 boost-libs boost --noconfirm
