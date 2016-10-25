FROM armv7/armhf-ubuntu_core:14.04

RUN echo "deb http://ports.ubuntu.com/ubuntu-ports/ trusty universe" >> /etc/apt/sources.list \
 && echo "deb-src http://ports.ubuntu.com/ubuntu-ports/ trusty universe" >> /etc/apt/sources.list \
 && echo "deb http://ports.ubuntu.com/ubuntu-ports/ trusty-updates universe" >> /etc/apt/sources.list \
 && echo "deb-src http://ports.ubuntu.com/ubuntu-ports/ trusty-updates universe" >> /etc/apt/sources.list \
 && apt-get -y update

RUN apt-get -y install g++ make wget qtbase5-dev pkg-config libmediainfo-dev \
 && cd /tmp \
 && wget https://github.com/QNapi/qnapi/releases/download/0.2.2/qnapi-0.2.2.tar.gz \
 && tar xf qnapi-0.2.2.tar.gz \
 && cd qnapi-0.2.2 \
 && /usr/lib/arm-linux-gnueabihf/qt5/bin/qmake \
 && make \
 && make install \
 && cd / \
 && rm -fr /tmp/qnapi* \
 && apt-get -y --purge autoremove g++ make wget pkg-config \
 && apt-get -y clean \
 && rm -fr /usr/share/doc* /usr/share/man /var/lib/apt /var/lib/dpkg /usr/lib/arm-linux-gnueabihf/qt5

ENTRYPOINT ["/usr/bin/qnapi", "-c"]
