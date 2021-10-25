
FROM ubuntu:20.04


#https://gnu-linux.org/installation-of-ns3-on-ubuntu.html
#RUN apt-get update -y && \
    # algum desses exige interação -> apt-get install -y vim python3 g++ python3-dev python3-pygccxml sqlite3 python3-setuptools git \
    # qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools qt5-default gir1.2-goocanvas-2.0 python3-gi python3-gi-cairo python3-pygraphviz gir1.2-gtk-3.0 ipython3 openmpi-bin
    # openmpi-common openmpi-doc libopenmpi-dev autoconf cvs bzr unrar gdb valgrind uncrustify doxygen graphviz imagemagick 
    # gsl-bin libgsl-dev libgslcblas0 tcpdump sqlite sqlite3 libsqlite3-dev libxml2 libxml2-dev cmake libc6-dev libc6-dev-i386 libclang-6.0-dev llvm-6.0-dev automake 
    # python3-pip libgtk-3-dev vtun lxc uml-utilities libxml2 libxml2-dev libboost-all-dev libgcrypt-dev
    #texlive texlive-extra-utils texlive-latex-extra texlive-font-utils dvipng latexmk &&
    # python3 -m pip install --user cxxfilt


    RUN curl -SL https://www.nsnam.org/releases/ns-allinone-3.35.tar.bz2 && tar xjf ns-allinone-3.35.tar.bz2 -d /ns3 && rm ns-allinone-3.35.tar.bz2
    RUN cd ns-allinone-3.35/ns-3.35 && /ns3/ns-allinone-3.35/ns-3.35/waf configure --enable-examples --enable-tests && /ns3/ns-allinone-3.35/ns-3.35/waf build
    
    USER ns3 
    WORKDIR /ns3

VOLUME [ "/ns3" ]
