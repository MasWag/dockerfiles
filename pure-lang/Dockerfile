FROM base/archlinux
MAINTAINER "Masaki Waga" <masakiwaga@gmail.com>
ENV container docker

# Update building environment
RUN pacman -Sy archlinux-keyring  --noconfirm
RUN pacman -Su --noconfirm
RUN pacman-db-upgrade
RUN trust extract-compat
RUN pacman -S --needed base-devel --noconfirm

# Install depending packages
RUN pacman -S gmp llvm35-libs mpfr readline llvm35 clang35 pcre --noconfirm

# Build PURE package
RUN useradd builder
RUN cd /tmp && sudo -u builder curl -L -O https://aur.archlinux.org/cgit/aur.git/snapshot/pure.tar.gz && sudo -u builder tar zxvf pure.tar.gz && cd pure && sudo -u builder makepkg -r

# Install PURE package
RUN pacman -U /tmp/pure/pure-*.pkg.tar.xz --noconfirm