FROM centos:7

ARG user_id
ARG user_name

RUN groupadd -g 911 exablaze && \
        groupadd -g 914 exadevel && \
        useradd -u ${user_id} -g users -G exablaze,exadevel -ms /bin/bash ${user_name}

RUN yum -y update && yum -y install python3 glibc-common texi2html texinfo chrpath
RUN yum -y install gawk make wget tar bzip2 gzip python unzip perl patch \
        iffutils diffstat git cpp gcc gcc-c++ glibc-devel texinfochrpath socat \
        perl-Data-Dumper perl-Text-ParseWords perl-Thread-Queue SDL-devel xterm	\
        which kernel-devel

RUN yum -y install less nano 

ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

USER ${user_name}

RUN mkdir -p /home/${user_name}/projects
WORKDIR /home/${user_name}/projects

RUN git clone git://git.openembedded.org/bitbake --branch 1.22
RUN git clone git://git.openembedded.org/openembedded-core --branch daisy
RUN git clone git://git.openembedded.org/meta-openembedded --branch daisy
