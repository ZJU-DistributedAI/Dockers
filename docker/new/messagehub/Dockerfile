FROM ubuntu:Xenial
MAINTAINER kingson"kingsonwill@zju.edu.cn"

WORKDIR /root
ENV GOROOT /usr/local/go
ENV GOPATH $HOME/go
ENV PATH $GOROOT/bin:$PATH


# install basic env
RUN apt-get install -y git && \
    apt-get install -y wget && \
    apt-get install -y gcc automake autoconf libtool make
RUN apt-get update -y

# install golang
ADD https://studygolang.com/dl/golang/go1.10.3.linux-amd64.tar.gz .
RUN tar -C /usr/local -xzf go1.10.3.linux-amd64.tar.gz && \
    mkdir go

# pull git
RUN cd ~ &&\
    git clone https://github.com/ZJU-DistributedAI/MessageHub



# clean local packages
RUN yum clean packages && \
    yum clean headers
CMD ["/bin/echo", "building succeed"]