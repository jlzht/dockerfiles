from debian:bullseye-slim

ARG USERID
ARG GROUPID

RUN groupadd -g $GROUPID dev && useradd -u $USERID -g $GROUPID -m dev # TODO: use ARGS instead

RUN apt update && apt install gawk wget git diffstat unzip \
      texinfo gcc build-essential chrpath socat cpio python3 \
      python3-pip python3-pexpect xz-utils debianutils \
      iputils-ping python3-git python3-jinja2 libegl1-mesa \
      libsdl1.2-dev python3-subunit mesa-common-dev zstd \
      liblz4-tool file locales libacl1 ncurses-base -y

ENV LANG=en_US.UTF-8
RUN sed -i -e "s/# $LANG.*/$LANG UTF-8/" /etc/locale.gen && \
    dpkg-reconfigure --frontend=noninteractive locales && \
    update-locale LANG=$LANG
