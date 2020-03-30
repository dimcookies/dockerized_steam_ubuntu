# dockerized_steam_ubuntu
Dockerized steam client on ubuntu 19.10

Inspired by https://github.com/kritzsie/steam-on-docker, a dockerized steam client based on vanilla ubuntu 19.10

**Known issues**
* No sound
* /home/steam/.local/share/Steam/ is created with roor privileges. Login manually and chown

*run* and *login* are symbolic links to *build*. build is an executable python 3 script that takes into account on the program name to work
