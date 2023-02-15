FROM ubuntu:22.04
ENV TINI_VERSION v0.19.0
LABEL maintainer="admin@cyberican.com"
LABEL version="1.0"
LABEL description="Simple Container For Spark"
RUN apt-get update -y && \
    apt-get install python3.10 -y && \
    apt-get install python3-pip -y && \
    pip3 install pyspark==3.3.0
RUN apt-get install software-properties-common -y && \
    add-apt-repository --yes ppa:openjdk-r/ppa && \
    apt-get update && apt-get install openjdk-17-jdk -y

ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /tini
RUN chmod +x /tini
ENTRYPOINT ["/tini", "-g", "--"]
ADD rund /
RUN chmod a+x /rund
CMD ["./rund"]
