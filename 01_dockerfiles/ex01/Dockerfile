#https://www.rosehosting.com/blog/how-to-set-up-a-teamspeak-server-on-ubuntu-16-04/

FROM debian

RUN apt-get update && apt-get upgrade

WORKDIR /usr/local
RUN wget http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2
RUN tar -jxvf teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2
RUN mv teamspeak3-server_linux_amd64 teamspeak
RUN chown -R teamspeak:teamspeak /usr/local/teamspeak
RUN ln -s /usr/local/teamspeak/ts3server_startscript.sh /etc/init.d/teamspeak
RUN update-rc.d teamspeak defaults