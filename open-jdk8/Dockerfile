FROM picoded/ubuntu-base
MAINTAINER hom liu <2624886248@qq.com>

# This is in accordance to : https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04
RUN add-apt-repository ppa:openjdk-r/ppa
RUN apt-get update
RUN apt-get install -y openjdk-8-jdk



# Setup JAVA_HOME, this is useful for docker commandline
#ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64/

RUN java -version