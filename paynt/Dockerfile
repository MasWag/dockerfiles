## This is the Dockerfile for paynt based on Arch Linux
FROM archlinux:base-devel

## Install yay to install dependencies (storm, graphviz, python3, and Z3) from AUR
RUN pacman -Syu --needed --noconfirm git base-devel jq sudo && useradd builduser -m && passwd -d builduser && printf 'builduser ALL=(ALL) ALL\n' | tee -a /etc/sudoers
USER builduser
RUN git clone https://aur.archlinux.org/yay.git /tmp/yay
WORKDIR /tmp/yay
RUN makepkg -si --noconfirm && yay -S --noconfirm storm graphviz python python-pip z3
USER root

# Install Paynt
RUN git clone https://github.com/randriu/synthesis.git /opt/paynt && pip3 install click z3-solver graphviz --no-cache-dir
WORKDIR /opt/paynt/payntbind
RUN pip3 install . --no-cache-dir
WORKDIR /opt/paynt
RUN pip3 install . --no-cache-dir

