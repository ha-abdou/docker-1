FROM debian

EXPOSE 9987/udp 10011 30033

ENV TS3SERVER_LICENSE=accept

ENV LD_LIBRARY_PATH=/opt/teamspeak

RUN DEBIAN_FRONTEND=noninteractive \
  apt-get -y update && \
  apt-get -y install bzip2 ca-certificates&& \
  apt-get clean

ADD http://dl.4players.de/ts/releases/3.4.0/teamspeak3-server_linux_amd64-3.4.0.tar.bz2 ./

RUN tar jxf teamspeak3-server_linux_amd64-3.4.0.tar.bz2 && \
       mv teamspeak3-server_linux_amd64 /opt/teamspeak && \
       rm teamspeak3-server_linux_amd64-3.4.0.tar.bz2

RUN echo 'cd /opt/teamspeak && ./ts3server logpath=/logs' > /opt/teamspeak/start.sh

CMD ["sh", "/opt/teamspeak/start.sh"]

#docker build -t ts_server .
#docker run -it --rm -p=9987:9987/udp  -p=10011:10011 -p=30033:30033 -d ts_server