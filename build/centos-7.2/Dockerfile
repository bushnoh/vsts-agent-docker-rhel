FROM centos:7.2.1511
ENV CENTOS_VERSION=7.2

RUN yum -y install \
       yum-plugin-ovl \
       deltarpm \
       epel-release \
       unzip \
       libunwind \
       gettext\
       libcurl-devel \
       openssl-devel \
       zlib \
       libicu-devel \
 && yum -y install \
       jq \
 && yum clean all

# This is needed to check out submodules
# https://gitlab.com/gitlab-org/gitlab-ci-multi-runner/issues/1914
RUN mkdir ~/.ssh/ \
 && echo -e "Host visualstudio.com\n	StrictHostKeyChecking no" > ~/.ssh/config

RUN localedef -i en_GB -f UTF-8 en_GB.UTF-8
RUN localedef -i en_US -f UTF-8 en_US.UTF-8

RUN echo 'LANG="en_GB.UTF-8"' > /etc/locale.conf 

WORKDIR /vsts

COPY ./start.sh .
RUN chmod +x start.sh

ENV LANG en_GB.UTF-8
ENV LANGUAGE en_GB:en
ENV LC_ALL en_GB.UTF-8

CMD ["./start.sh"]
