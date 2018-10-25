FROM ruby

EXPOSE 3000

RUN DEBIAN_FRONTEND=noninteractive\
    apt -y update &&\
	apt -y upgrade &&\
	apt install -y sqlite3

WORKDIR /tmp

RUN	curl -sL https://deb.nodesource.com/setup_8.x -o nodesource_setup.sh &&\
    sh nodesource_setup.sh &&\
    apt install -y nodejs

RUN curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - &&\
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list &&\
    apt update && apt install yarn

RUN apt clean

RUN mkdir -p /opt/app

WORKDIR /opt/app

ONBUILD ADD app /opt/app

ONBUILD RUN bundle install &&\
	rake db:migrate && rake db:seed
