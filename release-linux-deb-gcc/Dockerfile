ARG DISTRO=debian
ARG RELEASE=stretch
ARG ARCH=amd64
FROM openttd/base:linux-${DISTRO}-${RELEASE}-${ARCH}

ARG DISTRO
ARG RELEASE
ARG ARCH

# Compiler used in this Docker
RUN apt-get update && apt-get upgrade -y && apt-get dist-upgrade -y && \
    apt-get install -y --no-install-recommends \
    \
    binutils \
    g++ \
    gcc \
    && rm -rf /var/lib/apt/lists/*

# Dependencies needed to create deb files
RUN apt-get update && apt-get install -y --no-install-recommends \
    debhelper \
    fakeroot \
    && rm -rf /var/lib/apt/lists/*

COPY files/run.sh /usr/bin/

ENV DISTRO=${DISTRO} RELEASE=${RELEASE} ARCH=${ARCH}

WORKDIR /workdir/source

ENTRYPOINT ["run.sh"]
CMD ["dev"]
