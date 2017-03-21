FROM base/archlinux
MAINTAINER "Masaki Waga" <masakiwaga@gmail.com>
ENV container docker

WORKDIR /root
EXPOSE 5900 

ENV HOME /root
ENV GEOMETRY 1024x768
ENV DEPTH 16
ENV TZ Etc/UTC

RUN pacman -Sy archlinux-keyring  --noconfirm
RUN pacman -Syu --ignore ca-certificates --noconfirm
RUN pacman-db-upgrade
RUN pacman -S --force ca-certificates --noconfirm
RUN trust extract-compat
RUN pacman -S --needed base-devel --noconfirm
RUN pacman -S --force openbox tint2 tigervnc ttf-dejavu sudo --noconfirm

# Build obmenu-generator package
RUN useradd builder
RUN pacman -S perl-data-dump --noconfirm
RUN cd /tmp && sudo -u builder curl -L -O https://aur.archlinux.org/cgit/aur.git/snapshot/perl-linux-desktopfiles.tar.gz && sudo -u builder tar zxvf perl-linux-desktopfiles.tar.gz && cd perl-linux-desktopfiles && sudo -u builder makepkg -r
RUN pacman -U /tmp/perl-linux-desktopfiles/perl-linux-desktopfiles-*.pkg.tar.xz --noconfirm

RUN cd /tmp && sudo -u builder curl -L -O https://aur.archlinux.org/cgit/aur.git/snapshot/obmenu-generator.tar.gz && sudo -u builder tar zxvf obmenu-generator.tar.gz && cd obmenu-generator && sudo -u builder makepkg -r
RUN pacman -U /tmp/obmenu-generator/obmenu-generator-*.pkg.tar.xz --noconfirm

ADD xinitrc /etc/X11/xinit/xinitrc
ADD .config /root/.config
ADD xstartup /root/.vnc/xstartup
RUN chmod +x /root/.vnc/xstartup

RUN echo "root" | vncpasswd -f > /root/.vnc/passwd; \
    chmod 600 /root/.vnc/passwd

CMD ln -sf /usr/share/zoneinfo/$TZ /etc/localtime; vncserver -kill :0; vncserver :0 -geometry $GEOMETRY -depth $DEPTH; tail -f /root/.vnc/*.log