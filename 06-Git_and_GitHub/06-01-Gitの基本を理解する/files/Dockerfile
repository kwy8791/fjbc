FROM debian:stable-slim

ARG USERNAME=kwy8791
ARG PASSWORD=password
ARG SYSGRPNAME=sudo
ARG USERID=1000

ENV DEBIAN_FRONTEND noninteractiveRUN useradd -m --home-dir /home/${USERNAME}/ --groups ${SYSGRPNAME} --shell /bin/sh -u ${USERID} ${USERNAME}

RUN apt-get update -q -qq
RUN apt-get upgrade -q -qq
RUN useradd -m --home-dir /home/${USERNAME}/ --groups ${SYSGRPNAME} --shell /bin/sh -u ${USERID} ${USERNAME}
RUN mkdir -p /home/${USERNAME}/data
RUN chown -R ${USERNAME} /home/${USERNAME}/
RUN echo "${USERNAME}:${PASSWORD}" |/usr/sbin/chpasswd

RUN echo "root:Password" |/usr/sbin/chpasswd

RUN apt-get install sudo -q -qq -y
RUN add-apt-repository ppa:git-core/ppa
RUN apt-get update -q -qq
RUN apt-get upgrade -q -qq
RUN apt-get install git -q -qq -y

USER ${USERNAME}

WORKDIR /home/${USERNAME}/data

RUN /usr/bin/git config --global user.name "KAWAI, Yasuhiro"
RUN /usr/bin/git config --global user.email "k3iy6o@gmail.com"
RUN /usr/bin/git config --global core.quotepath false
RUN /usr/bin/git config --global core.pager "LESSCHARSET=utf-8 less"

RUN /bin/echo ':set encoding=utf-8'> ~/.vimrc
RUN /bin/echo ':set fileencodings=iso-2022-jp,euc-jp,sjis,utf-8' >> ~/.vimrc
RUN /bin/echo ':set fileformats=unix,dos,mac' >> ~/.vimrc

CMD /bin/bash
