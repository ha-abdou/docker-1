FROM ubuntu:16.04

EXPOSE 3000

RUN DEBIAN_FRONTEND=noninteractive apt -y update  &&\
	apt -y upgrade

RUN apt-get install -y \
    build-essential\
    git\
    fontconfig\
    libpng-dev\
    ruby\
    curl\
    ruby-dev

RUN gem install sass

#node
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash &&\
    apt-get install -y nodejs && alias node='nodejs'

#mongodb
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927 &&\
    echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.2 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-3.2.list &&\
    apt-get update &&\
    apt-get install -y mongodb-org

#bower gulp mean-cli
RUN npm install -g bower &&\
    npm install -g gulp &&\
    npm install -g yarn &&\
    npm install -g mean-cli

RUN apt clean

RUN mkdir -p /opt/app

WORKDIR /opt/app

ONBUILD ADD app /opt/app

ONBUILD RUN npm install && npm start

CMD ["bash"]
