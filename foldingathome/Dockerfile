# Dockerfile by johnktimsfrom https://hub.docker.com/r/johnktims/folding-at-home
# Downloaded 20.04.2020

FROM nvidia/cuda:9.2-base
LABEL maintainer="john.k.tims@gmail.com"

ENV FAH_VERSION_MINOR=7.6.9
ENV FAH_VERSION_MAJOR=7.6
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -qq update &&\
    apt-get -qq install --no-install-recommends --assume-yes \
        bzip2 \
        ca-certificates \
        clinfo \
        curl \
        ocl-icd-libopencl1 &&\
    useradd --create-home --uid 9999 --shell /usr/sbin/nologin --user-group folder &&\
        chmod 700 /home/folder &&\
    mkdir --parents /etc/OpenCL/vendors &&\
        ln --symbolic /usr/lib/x86_64-linux-gnu/libOpenCL.so.1 /usr/lib/x86_64-linux-gnu/libOpenCL.so &&\
        echo "libnvidia-opencl.so.1" > /etc/OpenCL/vendors/nvidia.icd &&\
    curl --output /tmp/fah.deb https://download.foldingathome.org/releases/public/release/fahclient/debian-stable-64bit/v${FAH_VERSION_MAJOR}/fahclient_${FAH_VERSION_MINOR}_amd64.deb &&\
        mkdir --parents /etc/fahclient/ &&\
        touch /etc/fahclient/config.xml &&\
        dpkg --install /tmp/fah.deb &&\
    apt-get -qq remove --assume-yes curl &&\
        apt-get -qq autoremove --assume-yes &&\
        rm -rf /tmp/* /var/log/* /var/lib/apt/ /var/cache/apt/

ENV NVIDIA_VISIBLE_DEVICES all
ENV NVIDIA_DRIVER_CAPABILITIES compute,utility

# Expose ports
EXPOSE 8080:7396 36331:36330

WORKDIR /home/folder
USER folder

ENV USER "Kristian_Reed"
ENV TEAM 254927
ENV POWER "medium"

COPY script.sh .
ENTRYPOINT ["/bin/bash", "./script.sh"]
