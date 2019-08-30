FROM ubuntu
RUN apt update && apt -y upgrade && apt install -y cowsay
ENTRYPOINT uptime | /usr/games/cowsay -f $(ls /usr/share/cowsay/cows/ | shuf -n1)