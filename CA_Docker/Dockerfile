FROM ubuntu:22.04

RUN apt-get update && apt-get install -y easy-rsa netcat
RUN useradd -m certificate_auth
USER certificate_auth
RUN mkdir /home/certificate_auth/easy-rsa
RUN ln -s /usr/share/easy-rsa/* /home/certificate_auth/easy-rsa/
RUN chmod 700 /home/certificate_auth/easy-rsa
WORKDIR /home/certificate_auth/easy-rsa
RUN ./easyrsa init-pki
COPY ./vars /home/certificate_auth/easy-rsa/vars
COPY ./server.py /home/certificate_auth/server.py
RUN (printf "\n" && cat) | ./easyrsa build-ca nopass