FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive

RUN  \
     apt-get install software-properties-common -y
RUN \
  echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
  add-apt-repository -y ppa:webupd8team/java && \
  apt-get update && \
  apt-get install -y oracle-java8-installer && \
  rm -rf /var/lib/apt/lists/* && \
  rm -rf /var/cache/oracle-jdk8-installer

RUN \
    wget http://ftp.unicamp.br/pub/apache/kafka/0.8.2.2/kafka_2.11-0.8.2.2.tgz && \
    tar -xvzf kafka_2.11-0.8.2.2.tgz && \
    mv kafka_2.11-0.8.2.2 kafka && \
    mv kafka /opt/
   
ADD server.properties /opt/kafka/config
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

EXPOSE 9092

ENTRYPOINT ["/opt/kafka/bin/kafka-server-start.sh"]
CMD ["/opt/kafka/config/server.properties"]

