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
RUN pacman -S --force openbox tint2 tigervnc --noconfirm

ADD xinitrc /etc/X11/xinit/xinitrc
ADD .config /root/.config
ADD xstartup /root/.vnc/xstartup

RUN echo "root" | vncpasswd -f > /root/.vnc/passwd; \
    chmod 600 /root/.vnc/passwd

CMD ln -sf /usr/share/zoneinfo/$TZ /etc/localtime; vncserver -kill :0; vncserver :0 -geometry $GEOMETRY -depth $DEPTH; tail -f /root/.vnc/*.log