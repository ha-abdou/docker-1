FROM ubuntu:16.04

EXPOSE 80 22 443

RUN DEBIAN_FRONTEND=noninteractive && apt-get update &&\
    apt-get install -yq --no-install-recommends ca-certificates curl openssh-server postfix tzdata

WORKDIR /tmp

RUN curl -LO https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh &&\
    bash /tmp/script.deb.sh

RUN EXTERNAL_URL="http://gitlab.example.com" apt-get install gitlab-ce

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN echo '/opt/gitlab/embedded/bin/runsvdir-start& gitlab-ctl reconfigure && sleep infinity' > ./start.sh

CMD ["bash", "./start.sh"]
#docker build -t gitlab .
#docker run -p 80:80 -p 42:22 -p 443:443 -d gitlab