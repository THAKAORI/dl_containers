FROM pytorch/pytorch:1.7.1-cuda11.0-cudnn8-devel

LABEL maintainer "Takahiro_Hori"

RUN apt-get update
RUN apt-get install -y openssh-server

RUN mkdir /var/run/sshd

RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config

RUN apt-get install -y git
RUN pip install opencv-python opencv-contrib-python
RUN apt-get install -y libgl1-mesa-dev
RUN apt-get install -y libglib2.0-0
RUN pip install tensorflow==1.15

COPY id_rsa_yairiws3.pub /root/authorized_keys

EXPOSE 22

CMD mkdir ~/.ssh && \
    mv ~/authorized_keys ~/.ssh/authorized_keys && \
    chmod 0600 ~/.ssh/authorized_keys && \
    /usr/sbin/sshd -D

