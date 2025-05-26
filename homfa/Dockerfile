FROM debian:bookworm-slim

LABEL maintainer="Masaki Waga <masakiwaga@gmail.com>" \
      org.opencontainers.image.source="https://github.com/virtualsecureplatform/homfa" \
      org.opencontainers.image.licenses="MIT" \
      org.opencontainers.image.title="HomFA" \
      org.opencontainers.image.description="HomFA: A tool for symbolic runtime monitoring using FHE"

ENV DEBIAN_FRONTEND=noninteractive

# Install dependencies and Spot
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        cmake make gcc g++ pkg-config libtbb-dev wget git ca-certificates gnupg && \
    wget -O /etc/apt/trusted.gpg.d/lrde.gpg https://www.lrde.epita.fr/repo/debian.gpg && \
    echo 'deb http://www.lrde.epita.fr/repo/debian/ stable/' >> /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y --no-install-recommends spot libspot-dev && \
    rm -rf /var/lib/apt/lists/*

# Clone and build HomFA
WORKDIR /tmp
RUN git clone --recursive --depth=1 https://github.com/virtualsecureplatform/homfa.git

WORKDIR /tmp/build
RUN cmake -S ../homfa -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr/local && \
    cmake --build . && \
    cmake --install . && \
    cd / && rm -rf /tmp/*

# Default entrypoint
CMD ["/usr/local/bin/homfa"]
