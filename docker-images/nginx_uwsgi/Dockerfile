FROM ubuntu:20.04

WORKDIR /app

RUN apt-get update && \
    export DEBIAN_FRONTEND=noninteractive && \
    apt install -yq tzdata supervisor nginx python3-pip default-libmysqlclient-dev && \
    ln -fs /usr/share/zoneinfo/America/Maceio /etc/localtime && \
    dpkg-reconfigure -f noninteractive tzdata

RUN mkdir -p /logs
COPY ./app /app
COPY ./configs /configs

RUN rm -f /etc/nginx/nginx.conf
RUN ln -s /configs/nginx_nginx.conf /etc/nginx/nginx.conf
RUN rm -f /etc/nginx/sites-enabled/default
RUN ln -s /configs/nginx_conf.d_nginx.conf /etc/nginx/conf.d/nginx.conf
RUN ln -s /configs/nginx_conf.d_upload.conf /etc/nginx/conf.d/upload.conf

RUN ln -s /configs/supervisord-burgueses.conf /etc/supervisor/conf.d/burgueses.conf
RUN chmod 755 /configs/supervisor-stop.sh
RUN ln -s /configs/supervisor-stop.sh /etc/supervisor/supervisor-stop.sh

RUN mkdir /etc/uwsgi
RUN ln -s /configs/uwsgi-main.ini /etc/uwsgi/uwsgi-main.ini

COPY ./entrypoint.sh /
RUN chmod 755 /entrypoint.sh
COPY ./start.sh /
RUN chmod 755 /start.sh

RUN pip3 install --upgrade pip
RUN pip3 install --no-cache-dir -r /app/requirements.txt

EXPOSE 80

ENTRYPOINT ["/entrypoint.sh"]

CMD ["/start.sh"]
