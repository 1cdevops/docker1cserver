FROM phusion/baseimage

RUN apt-add-repository multiverse
RUN apt-get update && apt-get install -y wget
RUN apt-get upgrade -y -o Dpkg::Options::="--force-confold"

RUN apt-get install -y unixodbc libgsf-1-114 imagemagick libglib2.0-dev t1utils
RUN echo ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true | debconf-set-selections
#RUN apt-get install libt1-5


RUN locale-gen ru_RU.UTF-8
RUN update-locale LANG=ru_RU.UTF-8

ENV SERVER_1C_VERSION 8.3.10-2168
ENV SERVER_1C_ARCH amd64
ENV DIST_SERVER_1C ./dist/

ADD ${DIST_SERVER_1C} /dist/

# common
RUN if [ ! -f /dist/1c-enterprise83-common_${SERVER_1C_VERSION}_${SERVER_1C_ARCH}.deb ]; then \
    echo File 1c-enterprise83-common_${SERVER_1C_VERSION}_${SERVER_1C_ARCH}.deb does not exist.; \
    echo "env DIST_SERVER_1C setted incorrectly. See README.md file."; \
    exit 1; fi

RUN if [ ! -f /dist/1c-enterprise83-common-nls_${SERVER_1C_VERSION}_${SERVER_1C_ARCH}.deb ]; then \
    echo File 1c-enterprise83-common_${SERVER_1C_VERSION}_${SERVER_1C_ARCH}.deb does not exist.; \
    echo "env DIST_SERVER_1C setted incorrectly. See README.md file."; \
    exit 1; fi
# server
RUN if [ ! -f /dist/1c-enterprise83-server_${SERVER_1C_VERSION}_${SERVER_1C_ARCH}.deb ]; then \
    echo File 1c-enterprise83-server_${SERVER_1C_VERSION}_${SERVER_1C_ARCH}.deb does not exist.; \
    echo "env DIST_SERVER_1C setted incorrectly. See README.md file."; \
    exit 1; fi

RUN if [ ! -f /dist/1c-enterprise83-server-nls_${SERVER_1C_VERSION}_${SERVER_1C_ARCH}.deb ]; then \
    echo File 1c-enterprise83-server_${SERVER_1C_VERSION}_${SERVER_1C_ARCH}.deb does not exist.; \
    echo "env DIST_SERVER_1C setted incorrectly. See README.md file."; \
    exit 1; fi

# install common
RUN dpkg -i /dist/1c-enterprise83-common_${SERVER_1C_VERSION}_${SERVER_1C_ARCH}.deb
RUN dpkg -i /dist/1c-enterprise83-common-nls_${SERVER_1C_VERSION}_${SERVER_1C_ARCH}.deb
# install server
RUN dpkg -i /dist/1c-enterprise83-server_${SERVER_1C_VERSION}_${SERVER_1C_ARCH}.deb
RUN dpkg -i /dist/1c-enterprise83-server-nls_${SERVER_1C_VERSION}_${SERVER_1C_ARCH}.deb





