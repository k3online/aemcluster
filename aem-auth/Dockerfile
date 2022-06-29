# Use linux base image 
FROM ubuntu:latest     

# Installing java 8 for the aem instance to work with
RUN apt-get update
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:openjdk-r/ppa
RUN apt-get update
RUN apt-get install less -y
RUN apt-get install -y curl
RUN apt-get install -y openjdk-8-jdk
RUN rm -rf /var/lib/apt/lists/*
RUN rm -rf /var/cache/oracle-jdk8-installer 

ENV localdir files
ENV cqjar cq-quickstart-6.5.0.jar

RUN mkdir /opt/aem

WORKDIR /opt/aem

ADD ${localdir}/${cqjar} /opt/aem/${cqjar}
ADD ${localdir}/license.properties /opt/aem/license.properties

EXPOSE 4502

CMD java -jar ${cqjar} -r author -p 4502 -Xmx1524M -Xms512M -XX:MaxPermSize=512M
