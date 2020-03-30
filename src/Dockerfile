FROM ubuntu:19.10

COPY steam.deb .

RUN dpkg --add-architecture i386

RUN apt-get update


#RUN apt install -y wget gdebi-core libgl1-mesa-glx:i386
RUN apt install -y gdebi-core libgl1-mesa-glx:i386

#RUN wget -O steam.deb http://media.steampowered.com/client/installer/steam.deb

RUN apt-get install -y tzdata keyboard-configuration
RUN gdebi  --non-interactive steam.deb

RUN apt-get install -y sudo

RUN adduser steam

RUN echo "steam ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/steam && chmod 0440 /etc/sudoers.d/steam

RUN su - steam -c "touch mine"


#CMD ["su", "-", "user", "-c", "steam"]

RUN apt install pciutils

RUN rm -rf /var/lib/apt/lists/*



RUN rm -rf /home/steam/.local
RUN mkdir -p /home/steam/.local/share/Steam
RUN chown -R steam:steam /home/steam/.local/
RUN chown -R steam:steam /home/steam/.local/share/
RUN chown -R steam:steam /home/steam/.local/share/Steam/


RUN apt update
RUN apt install -y alsa-base alsa-utils pulseaudio pulseaudio-utils libcanberra-pulse:amd64 libpulse-mainloop-glib0 libpulse0 libpulsedsp alsa-oss oss-compat libfftw3-bin libfftw3-dev
RUN rm -rf /var/lib/apt/lists/*

USER steam
ENV HOME /home/steam
WORKDIR /home/steam
VOLUME /home/steam

RUN cd /home/steam

CMD steam

