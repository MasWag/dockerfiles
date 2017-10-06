FROM base/archlinux
MAINTAINER "Masaki Waga" <masakiwaga@gmail.com>
ENV container docker

# Update building environment
RUN pacman -Sy archlinux-keyring  --noconfirm
RUN pacman -Su --noconfirm
RUN pacman-db-upgrade
RUN trust extract-compat

# Install depending packages
RUN pacman -S gcc5 make cmake bison flex eigen boost --noconfirm
