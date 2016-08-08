#
# Ubuntu Dockerfile
#
# https://github.com/dockerfile/ubuntu
#

# Pull base image.
FROM ubuntu:16.04
ENV HOME /home/action

RUN \
    sed -i 's/# \(.*multiverse$\)/\1/g' /etc/apt/sources.list && \
    apt-get update && \
    apt-get -y upgrade && \
    apt-get install -y build-essential && \
    apt-get install -y software-properties-common && \
    apt-get install -y \
        automake \
        autotools-dev \
        base-files \
        base-passwd \
        binutils \
        build-essential \
        bzip2 \
        cmake \
        cron \
        curl \
        dnsutils \
        gdb \
        git \
        git-core \
        gnupg \
        htop \
        imagemagick \
        libarchive-dev \
        libbz2-1.0 \
        libbz2-dev \
        libc6 \
        libcurl3 \
        libcurl3-gnutls \
        libcurl4-openssl-dev \
        libevent-1.4-2 \
        libevent-core-1.4-2 \
        libevent-dev \
        libevent-extra-1.4-2 \
        libffi-dev \
        libgdbm-dev \
        libglib2.0-dev \
        libicu-dev \
        libldap-2.4-2 \
        libldap2-dev \
        libltdl-dev \
        libltdl7 \
        liblzma-dev \
        liblzma-doc \
        liblzma5 \
        libmagickcore-dev \
        libmagickwand-dev \
        libmysqlclient-dev \
        libncap-dev \
        libncap44 \
        libncurses5-dev \
        libncursesw5 \
        libncursesw5-dev \
        libpam0g-dev \
        libpng12-0 \
        libpng12-dev \
        libpq-dev \
        libqt4-dev \
        libreadline-dev \
        libreadline6-dev \
        libsndfile1-dev \
        libsqlite3-dev \
        libxml2 \
        libxml2-dev \
        libxslt1-dev \
        libxt-dev \
        libxt6 \
        libyaml-dev \
        man \
        openssh-server \
        openssl \
        psmisc \
        ruby \
        s3cmd \
        screen \
        sqlite3 \
        sudo \
        telnet \
        unzip \
        util-linux \
        vim \
        wget \
        whiptail \
        xz-utils \
        zip \
        zlib1g \
        zlib1g-dev \
        zsh && \
    rm -rf /var/lib/apt/lists/*

ADD root/.bashrc /root/.bashrc
ADD root/.gitconfig /root/.gitconfig
ADD root/.scripts /root/.scripts

WORKDIR /home/action
RUN adduser --disabled-password action
RUN \
    sed -i "s/^#Protocol 2,1/Protocol 2/g" /etc/ssh/sshd_config && \
    sed -i "s/^#SyslogFacility AUTH/SyslogFacility AUTH/g" /etc/ssh/sshd_config && \
    sed -i "s/^\(PermitRootLogin yes\)/#\1\nPermitRootLogin without-password/g" /etc/ssh/sshd_config && \
    sed -i "s/^\(ChallengeResponseAuthentication no\)/#\1\nChallengeResponseAuthentication yes/g" /etc/ssh/sshd_config && \
    # sed -i "s/^\(#PasswordAuthentication yes\)/\1\nPasswordAuthentication yes/g" /etc/ssh/sshd_config && \
    sed -i "s/^\(PATH=\"\/usr\/local\/sbin:\/usr\/local\/bin:\/usr\/sbin:\/usr\/bin:\/sbin:\/bin:\/usr\/games\"\)$/\1\nLC_ALL=en_US.UTF-8/g" /etc/environment && \
RUN \
    chmod 640 /etc/sudoers && \
    sed -i "s/^\(# User privilege specification\)$/\1\naction  ALL=(ALL)       NOPASSWD:ALL/g" /etc/sudoers && \
    chmod 440 /etc/sudoers && \
echo 'action:nitrousio' | chpasswd && \
chsh -s /usr/bin/zsh action
RUN \
    chmod 775 /var/run/screen && \
    chmod 777 -R /var/spool/cron && \
    chown -R action:action /home/action
RUN locale-gen en_US.UTF-8

RUN mkdir -p /var/run/sshd
EXPOSE 22
CMD    /usr/sbin/sshd -D
