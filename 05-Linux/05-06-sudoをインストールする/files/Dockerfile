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

USER ${USERNAME}

WORKDIR /home/${USERNAME}/data

CMD /bin/bash
