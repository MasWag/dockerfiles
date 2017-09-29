FROM base/archlinux
MAINTAINER "Masaki Waga" <masakiwaga@gmail.com>
ENV container docker

# Update building environment
RUN pacman -Sy archlinux-keyring  --noconfirm
RUN pacman -Su --noconfirm
RUN pacman-db-upgrade
RUN trust extract-compat

# Install depending packages
RUN pacman -S wget --noconfirm

# Download install-tl
RUN cd /tmp && wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz && tar zxvf install-tl-unx.tar.gz
RUN yes I | /tmp/install-tl*/install-tl --repository http://mirror.ctan.org/systems/texlive/tlnet/
