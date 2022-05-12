FROM ubuntu:20.04

WORKDIR /ciclope/app

RUN apt-get update && \
    export DEBIAN_FRONTEND=noninteractive && \
    apt install -yq tzdata supervisor nginx python3-pip default-libmysqlclient-dev && \
    ln -fs /usr/share/zoneinfo/America/Maceio /etc/localtime && \
    dpkg-reconfigure -f noninteractive tzdata



COPY ./entrypoint.sh /
RUN chmod 755 /entrypoint.sh
COPY ./start.sh /
RUN chmod 755 /start.sh

RUN pip3 install --upgrade pip


EXPOSE 80

ENTRYPOINT ["/entrypoint.sh"]

#CMD ["/start.sh"]
CMD ["bash"]