FROM ubuntu:20.04

#offline option of deb package
#COPY steam.deb .

RUN dpkg --add-architecture i386

RUN apt-get update

#adding tzdata and keyboard-configuration here since it requires user input and gdebi blocks
RUN apt install -y wget gdebi-core libgl1-mesa-glx:i386 tzdata keyboard-configuration sudo pciutils

RUN wget -O steam.deb http://media.steampowered.com/client/installer/steam.deb

RUN gdebi  --non-interactive steam.deb

RUN adduser steam
RUN echo "steam ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/steam && chmod 0440 /etc/sudoers.d/steam

RUN mkdir -p /home/steam/.local/share/Steam
#this does not seems to work, when docker runs this is owned by root
#login into docker and manually perform the command
RUN chown -R steam:steam /home/steam/.local/

#attempt to fix sound
RUN apt install -y alsa-base alsa-utils pulseaudio pulseaudio-utils libcanberra-pulse:amd64 libpulse-mainloop-glib0 libpulse0 libpulsedsp alsa-oss oss-compat libfftw3-bin libfftw3-dev

RUN rm -rf /var/lib/apt/lists/*

USER steam
ENV HOME /home/steam
WORKDIR /home/steam
VOLUME /home/steam

RUN cd /home/steam
CMD steam

