FROM ubuntu:focal

RUN echo "deb http://archive.ubuntu.com/ubuntu focal main universe" > /etc/apt/sources.list
RUN apt-get update
RUN apt-get upgrade -y

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get install -y software-properties-common -f
RUN add-apt-repository -y ppa:webupd8team/java

RUN apt-get update
RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections

RUN apt-get install -y openjdk-8-jdk
RUN apt-get install -y wget
RUN apt-get install -y unzip

RUN mkdir /minecraft
RUN wget -O /tmp/tekkit.zip http://servers.technicpack.net/Technic/servers/tekkitmain/Tekkit_Server_v1.2.9g-2.zip
RUN unzip /tmp/tekkit.zip -d /minecraft/

ADD ./launch.sh /minecraft/launch.sh
RUN chmod +x /minecraft/launch.sh

VOLUME /minecraft
EXPOSE 25565

WORKDIR /minecraft
ENTRYPOINT ["/minecraft/launch.sh"]
