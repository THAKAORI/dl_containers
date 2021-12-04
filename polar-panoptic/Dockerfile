FROM pytorch/pytorch:1.9.1-cuda11.1-cudnn8-devel

LABEL maintainer "Takahiro_Hori"

RUN apt-get update
RUN apt-get install -y openssh-server

RUN mkdir /var/run/sshd

RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config

RUN apt-get install -y git

COPY id_rsa.pub /root/authorized_keys

EXPOSE 22

RUN mkdir /root/.ssh
RUN mv /root/authorized_keys /root/.ssh/authorized_keys
RUN chmod 0600 /root/.ssh/authorized_keys

CMD /usr/sbin/sshd -D

