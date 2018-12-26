FROM nginx:1.15.7

MAINTAINER Nithin Madhuranga <nithin@axis.lk>

RUN apt update && \
    apt install openssl && \
    apt install wget -y && \
    apt install make && \
    apt install libnss3-tools -y

RUN cd tmp && \
    wget https://github.com/FiloSottile/mkcert/releases/download/v1.1.2/mkcert-v1.1.2-linux-amd64 && \
    mv mkcert-v1.1.2-linux-amd64 mkcert  && \
    chmod +x mkcert && \
    cp mkcert /usr/local/bin/ && \
    cd /usr/local/bin && \
    mkcert -install && \
    mkcert dev.local '*.dev.local' localhost 127.0.0.1 ::1 && \
    ls

COPY ./default.conf /etc/nginx/conf.d/default.conf
