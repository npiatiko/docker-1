FROM ubuntu:16.04
RUN apt update && apt upgrade -y
RUN apt install -y libncurses5-dev libncursesw5-dev build-essential clang emacs vim
COPY app /app/
CMD bash