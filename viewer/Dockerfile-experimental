FROM theiaide/sadl:next

RUN git clone https://gitlab.com/graphviz/graphviz /usr/graphviz

RUN apk update
RUN apk add g++ libtool automake make autoconf-archive autoconf python3 libcurl pkgconfig libltdl bison flex
RUN alias yacc="bison"

WORKDIR /usr/graphviz
RUN ./autogen.sh
RUN ./configure
RUN make
RUN make install

ENV GraphVizPath /usr/local/bin
ENV GraphVizKeepDot true

WORKDIR /home/theia
