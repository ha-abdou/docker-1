FROM ubuntu:16.04

RUN DEBIAN_FRONTEND=noninteractive apt -y update  &&\
	apt -y upgrade

RUN apt-get install -y \
    git\
    gcc\
    build-essential\
    curl

WORKDIR /var/code

COPY code /var/code

CMD ["bash"]