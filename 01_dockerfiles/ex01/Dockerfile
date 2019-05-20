FROM debian
EXPOSE 9987/udp
EXPOSE 10011/tcp
EXPOSE 30033/tcp
ENV TS3SERVER_LICENSE=accept
RUN apt-get update -y && apt-get install wget -y && apt-get install bzip2 -y
RUN groupadd -r teamspeak && \
	useradd -r -m -g teamspeak teamspeak
USER teamspeak

WORKDIR /home/teamspeak

RUN wget https://files.teamspeak-services.com/releases/server/3.6.1/teamspeak3-server_linux_amd64-3.6.1.tar.bz2 \
&& bzip2 -d teamspeak3-server_linux_amd64-3.6.1.tar.bz2 \ 
&& tar -xf teamspeak3-server_linux_amd64-3.6.1.tar \
&& rm teamspeak3-server_linux_amd64-3.6.1.tar

WORKDIR /home/teamspeak/teamspeak3-server_linux_amd64
ENTRYPOINT ["sh", "ts3server_minimal_runscript.sh", "createinifile=1"]
#https://console.nodilex.com/fr/community/tutorials/13/installer-un-serveur-vocal-teamspeak-3-sur-linux-debian-ubuntu/

#docker build -t ex02:v1 .
#docker run -it -p 9987:9987/udp -p 10011:10011 -p 30033:30033 --rm ex02:v1
#Teamspeak : #  9987 default voice
# 10011 server query
# 30033 file transport
