FROM mcr.microsoft.com/dotnet-buildtools/prereqs:fedora-29

# Install Helix Dependencies

RUN dnf install -y \
        python2-devel \
        redhat-rpm-config \        
        sudo \
    && dnf clean all

RUN python -m pip install --upgrade pip==19.0.3 && \
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

# Needed for .NET corefx tests to pass
ENV LANG=en-US.UTF-8

# create helixbot user and give rights to sudo without password
RUN /usr/sbin/useradd -G adm -s /bin/sh helixbot; \
    chmod 755 /root ; \
    echo "helixbot ALL=(ALL)       NOPASSWD: ALL" > /etc/sudoers

USER helixbot
