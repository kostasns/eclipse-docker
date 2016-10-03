FROM buildpack-deps:jessie-curl
MAINTAINER Kostas <kostas@nuclearshoebox.com>

#Installing TINI, the PID 1 process for sub-process reaping
ENV TINI_VERSION v0.10.0
ENV TINI_SHA1 03e12f4652c4afb252dbb18a305d0c3e6ec1a43d

RUN curl -fsSL https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini -o /bin/tini && \
    chmod +x /bin/tini && echo "${TINI_SHA1} /bin/tini" | sha1sum -c -

#Installing JAVA
RUN echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main" | tee /etc/apt/sources.list.d/webupd8team-java.list && \
    echo "deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main" | tee -a /etc/apt/sources.list.d/webupd8team-java.list && \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys EEA14886 && \
    apt-get update && echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections && \
    apt-get install -y \
     oracle-java8-installer \
     oracle-java8-set-default \
     libgtk2.0-0:amd64 \
     libxtst6 

#Installing eclipse
ENV ECLIPSE_URL http://ftp.snt.utwente.nl/pub/software/eclipse//technology/epp/downloads/release/kepler/SR2/eclipse-jee-kepler-SR2-linux-gtk-x86_64.tar.gz
ENV ECLIPSE_SHA1 22986dc814c175284ea4419cb9cbee6997eb19ca
ENV ECLIPSE_HOME /eclipse

RUN mkdir -p ${ECLIPSE_HOME} && \
    curl -fsSL ${ECLIPSE_URL} -o /tmp/eclipse.tar.gz && \
    echo "${ECLIPSE_SHA1} /tmp/eclipse.tar.gz" | sha1sum -c - && \
    tar -zxf /tmp/eclipse.tar.gz -C /tmp/ && \
    mv -f /tmp/eclipse/* ${ECLIPSE_HOME} && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /var/cache/*
	
ENTRYPOINT ["/bin/tini", "--"]
CMD ${ECLIPSE_HOME}/eclipse