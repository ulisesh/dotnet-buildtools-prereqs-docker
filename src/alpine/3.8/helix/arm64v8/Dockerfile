FROM arm64v8/alpine:3.8

# Install .NET Core Dependencies for Alpine

RUN apk update && \
    apk add --no-cache \
        autoconf \
        bash \
        build-base \
        clang \
        clang-dev \
        cmake \
        coreutils \
        curl \
        gcc \
        gettext-dev \
        git \
        icu-dev \
        iputils \
        krb5-dev \
        libffi \
        libffi-dev \
        libtool \
        libunwind-dev \        
        linux-headers \
        llvm \
        make \
        openssl \
        openssl-dev \
        paxctl \        
        python \
        python-dev \
        py-cffi \
        py-pip \        
        sudo \
        tzdata \
        util-linux-dev \
        wget \
        which \        
        zlib-dev && \
    apk -X http://dl-cdn.alpinelinux.org/alpine/edge/main add --no-cache \
        lttng-ust-dev \
        userspace-rcu-dev        

# Install Helix Dependencies

RUN python -m pip install --upgrade pip==19.0.2 && \
    python -m pip install \ 
        applicationinsights==0.11.7 \
        certifi==2018.11.29 \
        cryptography==2.5 \                  
        docker==3.6.0 \
        ndg-httpsclient==0.5.1  \
        psutil==5.4.8 \
        pyasn1==0.4.5 \
        pyopenssl==18.0.0 \
        requests==2.21.0 \
        six==1.12.0 \
        virtualenv==16.2.0

# create helixbot user and give rights to sudo without password
RUN /usr/sbin/adduser -D -u 1001 -G adm -s /bin/sh helixbot; \
    chmod 755 /root ; \
    echo "helixbot ALL=(ALL)       NOPASSWD: ALL" > /etc/sudoers.d/helixbot

USER helixbot