FROM ubuntu:xenial
MAINTAINER kingson"kingsonwill@zju.edu.cn"

WORKDIR /root
ENV GOROOT /usr/local/go
ENV GOPATH $HOME/go
ENV PATH $GOROOT/bin:$PATH


# install basic env
RUN apt-get update -y && \
    apt-get install -y git && \
    apt-get install -y wget && \
    apt-get install -y gcc automake autoconf libtool make
RUN apt-get update -y


#install golang
ADD https://studygolang.com/dl/golang/go1.10.3.linux-amd64.tar.gz .
RUN tar -C /usr/local -xzf go1.10.3.linux-amd64.tar.gz && \
    mkdir go


# build geth
RUN cd ~ &&\
    git clone https://github.com/ethereum/go-ethereum 
RUN cd go-ethereum && \
    make geth && \
    cd ~ && \
    mkdir geth && \
    cd geth && \
    mkdir chain


# input geneis
RUN cd geth && \
    touch genesis.json && \
    echo  "{" > genesis.json && \
    echo  "\t\"config\": {" >> genesis.json && \
    echo  "\t\t\"chainId\": 20," >> genesis.json && \
    echo  "\t\t\"homesteadBlock\": 0," >> genesis.json && \
    echo  "\t\t\"eip155Block\": 0," >> genesis.json && \
    echo  "\t\t\"eip158Block\": 0" >> genesis.json && \
    echo  "\t}," >> genesis.json && \
    echo  "\t\"alloc\": {" >> genesis.json && \
    echo  "\t\t\"bc9a3ece02d7cb31cf63dfdfc48db0b82770d014\": {" >> genesis.json && \
    echo  "\t\t\t\"balance\": \"1000000000000000000000000000000\"" >> genesis.json && \
    echo  "\t\t}," >> genesis.json && \
    echo  "\t\t\"457e7d69fd3ac576aa744228e6b3319cde768473\": {" >> genesis.json && \
    echo  "\t\t\t\"balance\": \"2000000000000000000000000000000\"" >> genesis.json && \
    echo  "\t\t}," >> genesis.json && \
    echo  "\t\t\"926ef6011f7c852d30a01c7a4aaa5cbc460588fc\": {" >> genesis.json && \
    echo  "\t\t\t\"balance\": \"3000000000000000000000000000000\"" >> genesis.json && \
    echo  "\t\t}" >> genesis.json && \
    echo  "\t}," >> genesis.json && \
    echo  "\t\"nonce\": \"0x0000000000000056\"," >> genesis.json && \
    echo  "\t\"difficulty\": \"0x020000\"," >> genesis.json && \
    echo  "\t\"mixhash\": \"0x0000000000000000000000000000000000000000000000000000000000000000\"," >> genesis.json && \
    echo  "\t\"coinbase\": \"0x0000000000000000000000000000000000000000\"," >> genesis.json && \
    echo  "\t\"timestamp\": \"0x00\"," >> genesis.json && \
    echo  "\t\"parentHash\": \"0x0000000000000000000000000000000000000000000000000000000000000000\"," >> genesis.json && \
    echo  "\t\"extraData\": \"0x11bbe8db4e347b4e8c937c1c8370e4b5ed33adb3db69cbdb7a38e1e50b1b82fa\"," >> genesis.json && \
    echo  "\t\"gasLimit\": \"0xffffffff\"" >> genesis.json && \
    echo  "}" >> genesis.json



VOLUME ./geth:~/

EXPOSE 16333 8545

# clean local packages
RUN apt-get autoclean -y && \
    apt-get clean -y && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
CMD ["/bin/echo", "building succeed"]
