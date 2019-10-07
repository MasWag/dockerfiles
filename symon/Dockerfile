FROM alpine:3.10.2
MAINTAINER "Masaki Waga" <masakiwaga@gmail.com>

# Install depending packages
RUN apk add --no-cache g++ make cmake bison flex-dev boost-dev doxygen git libgmpxx gmp-dev

# Download the PPL source
RUN wget https://www.bugseng.com/products/ppl/download/ftp/releases/1.2/ppl-1.2.tar.xz

# Build PPL
RUN tar xvf ppl-1.2.tar.xz && cd ppl-1.2 && ./configure && make && make install
# --disable-dependency-tracking --enable-coefficients=checked-int64 --disable-silent-rules --enable-optimization=speed

# Download and Build SyMon
RUN git clone https://github.com/MasWag/symon.git && mkdir -p symon/build && cd symon/build && cmake -DCMAKE_BUILD_TYPE=Release .. && make symon && make install

# Install build only dependencies
RUN apk del --no-cache make cmake bison flex doxygen git
RUN rm -rf /symon /ppl-1.2

ENTRYPOINT ["/usr/local/bin/symon"]