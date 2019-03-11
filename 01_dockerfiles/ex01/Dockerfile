# From a debian image you will add the appropriate sources to create a TeamSpeak server, that will launch along with your container. It will be d# eemed valid if at least one user can connect to it and engage in a normal discussion (no far-fetched setup), so be sure to create your Dockerfi# le with the right options. Your program should get the sources when it builds, they cannot be in your repository

FROM debian

ENV TS3SERVER_LICENSE=accept

WORKDIR /home/teamspeak

EXPOSE 9987/udp 10011 30033

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y wget bzip2 && \
    wget http://dl.4players.de/ts/releases/3.0.13.4/teamspeak3-server_linux_amd64-3.0.13.4.tar.bz2 && \
    tar xvf teamspeak3-server_linux_amd64-3.0.13.4.tar.bz2 && \
	rm teamspeak3-server_linux_amd64-3.2.0.tar.bz2

CMD ["sh", "teamspeak3-server_linux_amd64/ts3server_minimal_runscript.sh"]

# docker build -t ex01 .
# docker run -it --rm --name ex1 -e TS3SERVER_LICENSE=accept -p 9987:9987/udp -p 10011:10011 -p 30033:30033 teamspeak
