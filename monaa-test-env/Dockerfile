FROM archlinux/archlinux
MAINTAINER "Masaki Waga" <masakiwaga@gmail.com>
ENV container docker

# WORKAROUND for glibc 2.33 and old Docker
# See https://github.com/actions/virtual-environments/issues/2658
# Thanks to https://github.com/lxqt/lxqt-panel/pull/1562
RUN patched_glibc=glibc-linux4-2.33-4-x86_64.pkg.tar.zst && \
    curl -LO "https://repo.archlinuxcn.org/x86_64/$patched_glibc" && \
    bsdtar -C / -xvf "$patched_glibc"

# Update building environment
RUN pacman -Sy archlinux-keyring  --noconfirm
RUN pacman -Su --noconfirm
RUN pacman-db-upgrade
RUN trust extract-compat

# Install depending packages
RUN pacman -Sy --needed base-devel make cmake bison flex eigen boost clang doxygen git ppl --noconfirm
