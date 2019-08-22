FROM alpine
LABEL maintainer="npiatiko@student.unit.ua"
RUN apk update && apk upgrade && apk add emacs && apk add bash
CMD emacs
#to build use command 'docker build --tag=ex00 .'
#to run use command 'docker run -ti ex00'