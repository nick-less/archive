# esp-sdk 
FROM ubuntu:16.04
MAINTAINER <nick-less@gmx.de>
# install tools required by sdk
RUN apt-get update && apt-get install -y \
	make unrar-free autoconf automake libtool gcc g++ gperf \
    flex bison texinfo gawk ncurses-dev libexpat-dev python-dev python python-serial \
    sed git unzip bash help2man wget bzip2 libtool-bin git
# add an user, sdk wont build as root
RUN useradd -ms /bin/bash sdkbuilder
USER sdkbuilder
WORKDIR /home/sdkbuilder
# clone sdk
RUN git clone --recursive https://github.com/pfalcon/esp-open-sdk.git
WORKDIR /home/sdkbuilder/esp-open-sdk
RUN make toolchain esptool libhal STANDALONE=n
ENV PATH="/home/sdkbuilder/esp-open-sdk/xtensa-lx106-elf/bin:${PATH}"

# build
# docker run -it cross/esp8266
# run
# docker run -v <localpath>:<containerpath> -it cross/esp8266