FROM debian
EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011
EXPOSE 41144

RUN useradd teamspeak && mkdir /home/teamspeak && chown teamspeak:teamspeak /home/teamspeak
WORKDIR /home/teamspeak 
RUN apt-get update -y && apt-get upgrade -y && \
	apt-get install bzip2 wget -y && \
	wget http://dl.4players.de/ts/releases/3.0.13.8/teamspeak3-server_linux_amd64-3.0.13.8.tar.bz2 && \
	bunzip2 *.bz2 && \
	tar -xvf *.tar
COPY ts3.ini /home/teamspeak/teamspeak3-server_linux_amd64/ts3.ini
USER teamspeak
ENTRYPOINT ["sh", "teamspeak3-server_linux_amd64/ts3server_minimal_runscript.sh","inifile=ts3.ini"]