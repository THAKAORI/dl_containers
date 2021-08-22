FROM pytorch/pytorch:latest

LABEL maintainer "Takahiro_Hori"

RUN apt-get update
RUN apt-get install -y openssh-server

RUN mkdir /var/run/sshd

RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config

RUN apt-get install -y git

COPY id_rsa_yairiws3.pub /root/authorized_keys

EXPOSE 22

CMD mkdir ~/.ssh && \
    mv ~/authorized_keys ~/.ssh/authorized_keys && \
    chmod 0600 ~/.ssh/authorized_keys && \
    /usr/sbin/sshd -D

