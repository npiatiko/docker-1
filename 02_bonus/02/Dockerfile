FROM debian
RUN dpkg --add-architecture i386 && \
	apt update && apt -y upgrade && \
	apt install -y libc6:i386 wget && \
	mkdir /opt/steam
WORKDIR /opt/steam
RUN wget http://media.steampowered.com/client/steamcmd_linux.tar.gz && \
	tar -zxvf steamcmd_linux.tar.gz && rm -f steamcmd_linux.tar.gz
RUN /opt/steam/steamcmd.sh +login anonymous +force_install_dir /opt/hlds +app_update 90 validate +quit || true && \
	/opt/steam/steamcmd.sh +login anonymous +force_install_dir /opt/hlds +app_update 90 validate +quit
RUN ln -s /opt/steam/linux32/ ~/.steam/sdk32
WORKDIR /opt/hlds
RUN touch listip.cfg banned.cfg
EXPOSE 27015
ENTRYPOINT ./hlds_run -game cstrike +maxplayers 20 +map de_dust2
#CMD bash

#docker build -t cs .
#docker run -ti --rm -p 27015:27015 cs