FROM archlinux/base
MAINTAINER "Masaki Waga" <masakiwaga@gmail.com>
ENV container docker

# Update building environment
RUN pacman -Sy archlinux-keyring  --noconfirm
RUN pacman -Su --noconfirm
RUN pacman-db-upgrade
RUN trust extract-compat

# Install depending packages
RUN pacman -Sy --needed base-devel make cmake bison flex eigen boost clang doxygen git ppl --noconfirm
