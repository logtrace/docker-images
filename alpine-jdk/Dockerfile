FROM sithum/alpine:3.6
# Official Alpine linux base, see URL below for more info
# https://github.com/docker-library/official-images/tree/master/library

MAINTAINER Sithum Nissanka <sithum.nissanka@ebuilder.com>

# Control the java versions to be grabbed from oracle
ENV JAVA_VERSION=8u171 \
    JAVA_MINOR_VERSION=b15 \
    JAVA_DISTRO=jdk \
    JAVA_INSTALL_DIR=jdk1.8.0_171

COPY ${JAVA_DISTRO}-${JAVA_VERSION}-linux-x64.tar.gz ${JAVA_DISTRO}-${JAVA_VERSION}-linux-x64.tar.gz

# Get and install oracle correctly (based on version above)
RUN apk add --no-cache --virtual=build-dependencies wget ca-certificates tar && \
    mkdir /opt && \
    #wget --header "Cookie: oraclelicense=accept-securebackup-cookie;" \
    #     http://download.oracle.com/otn-pub/java/${JAVA_DISTRO}/${JAVA_VERSION}-${JAVA_MINOR_VERSION}/${JAVA_DISTRO}-${JAVA_VERSION}-linux-x64.tar.gz && \
    cp ${JAVA_DISTRO}-${JAVA_VERSION}-linux-x64.tar.gz /opt && \
    cd /opt && \
    tar xfvz ${JAVA_DISTRO}-${JAVA_VERSION}-linux-x64.tar.gz && \
    rm ${JAVA_DISTRO}-${JAVA_VERSION}-linux-x64.tar.gz && \
    cd /opt/${JAVA_INSTALL_DIR} && \
    rm -rf *src.zip \
          lib/missioncontrol \
          lib/visualvm \
          lib/*javafx* \
          jre/lib/plugin.jar \
          jre/lib/ext/jfxrt.jar \
          jre/bin/javaws \
          jre/lib/javaws.jar \
          jre/lib/desktop \
          jre/plugin \
          jre/lib/deploy* \
          jre/lib/*javafx* \
          jre/lib/*jfx* \
          jre/lib/amd64/libdecora_sse.so \
          jre/lib/amd64/libprism_*.so \
          jre/lib/amd64/libfxplugins.so \
          jre/lib/amd64/libglass.so \
          jre/lib/amd64/libgstreamer-lite.so \
          jre/lib/amd64/libjavafx*.so \
          jre/lib/amd64/libjfx*.so && \
    \
    #apk del build-dependencies && \
    export JAVA_HOME=`pwd` && \
    export PATH=$PATH:$JAVA_HOME/bin
