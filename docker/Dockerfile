FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive
ENV DEBCONF_NONINTERACTIVE_SEEN=true

#Referência -> https://gnu-linux.org/installation-of-ns3-on-ubuntu.html
RUN apt-get update -y && \
    apt-get install -y python3 g++ python3-dev python3-pygccxml sqlite3 python3-setuptools python3-gi python3-gi-cairo python3-pygraphviz python3-pip ipython3 \
    qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools qt5-default \
    gir1.2-goocanvas-2.0  gir1.2-gtk-3.0  openmpi-bin openmpi-common openmpi-doc gsl-bin \
    libopenmpi-dev autoconf cvs bzr unrar gdb valgrind uncrustify doxygen graphviz imagemagick \
    libgsl-dev libgslcblas0 tcpdump sqlite sqlite3 libsqlite3-dev libxml2 libxml2-dev cmake libc6-dev libc6-dev-i386 libclang-6.0-dev llvm-6.0-dev automake \
    libgtk-3-dev vtun lxc uml-utilities libxml2 libxml2-dev libboost-all-dev libgcrypt-dev \
    texlive texlive-extra-utils texlive-latex-extra texlive-font-utils dvipng latexmk wget && \
    python3 -m pip install --user cxxfilt
    # git \

RUN rm -f /etc/localtime && ln -s  /usr/share/zoneinfo/America/Sao_Paulo  /etc/localtime

RUN useradd -ms /bin/bash ns3

ADD https://www.nsnam.org/releases/ns-allinone-3.35.tar.bz2 /tmp/ns-allinone-3.35.tar.bz2
RUN cd /tmp && tar xjf /tmp/ns-allinone-3.35.tar.bz2 -C /home/ns3 && \
    cd /home/ns3/ns-allinone-3.35/ns-3.35 && \
    ./waf configure --build-profile=optimized --enable-examples --enable-tests && \
    cd /home/ns3/ns-allinone-3.35/ && \
    ./build.py -- --disable-python
    
# Testar:
# RUN cd /tmp && tar xjf /tmp/ns-allinone-3.35.tar.bz2 -C /home/ns3 && \
#    cd /home/ns3/ns-allinone-3.35/ && \
#    ./build.py -- --disable-python
#
# RUN cd /home/ns3/ns-allinone-3.35/ns-3.35 && \
#    ./waf configure --build-profile=optimized --enable-examples --enable-tests && 
#    ./waf build

#Cleanup
RUN rm -f /tmp/* && \
    apt-get clean && \
    rm -rf /var/lib/apt

USER ns3
WORKDIR /home/ns3
VOLUME [ "/home/ns3" ]
