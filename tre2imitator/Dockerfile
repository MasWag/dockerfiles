FROM maswag/monaa2imitator
MAINTAINER "Masaki Waga" <masakiwaga@gmail.com>

# Install depending packages
RUN apt-get update && apt-get install -y \
    g++ \
    make \
    cmake \
    bison \
    flex \
    libboost-dev \
    libboost-graph1.65.1\
    libboost-graph1.65-dev\
    libboost-iostreams1.65.1\
    libboost-iostreams1.65-dev\
    libboost-program-options1.65.1\
    libboost-program-options1.65-dev\
    libeigen3-dev \
    doxygen \
    git

# Download the MONAA source
RUN git clone https://github.com/MasWag/monaa.git

# Build and Install tre2ta
RUN mkdir -p monaa/build && cd monaa/build && cmake -DCMAKE_MODULE_PATH=/eigen/cmake -DCMAKE_BUILD_TYPE=Release .. && make tre2ta && install -m755 tre2ta /usr/local/bin

# Install build only dependencies
RUN apt-get remove -y\
    bison\
    cmake\
    doxygen\
    flex\
    git\
    g++ \
    libboost-dev\
    libboost-graph1.65-dev\
    libboost-iostreams1.65-dev\
    libboost-iostreams1.65.1\
    libboost-program-options1.65-dev\
    libeigen3-dev\
    make && apt-get clean -y && apt-get autoremove -y && rm -rf /monaa

COPY tre2imitator /usr/local/bin/tre2imitator
ENTRYPOINT ["/usr/local/bin/tre2imitator"]