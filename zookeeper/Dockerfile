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
    wget http://ftp.unicamp.br/pub/apache/zookeeper/zookeeper-3.3.6/zookeeper-3.3.6.tar.gz && \
    tar -xvzf zookeeper-3.3.6.tar.gz && \
    mv zookeeper-3.3.6 zookeeper && \
    mv zookeeper /opt/
   
ADD zoo.cfg /opt/zookeeper/conf/ 
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

EXPOSE 2181

ENTRYPOINT ["/opt/zookeeper/bin/zkServer.sh"]
CMD ["start-foreground"]

