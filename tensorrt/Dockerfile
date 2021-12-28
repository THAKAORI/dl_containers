FROM nvcr.io/nvidia/tensorrt:21.11-py3

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
RUN pip install scipy matplotlib

COPY id_rsa.pub /root/authorized_keys

EXPOSE 22

RUN mkdir /root/.ssh
RUN mv /root/authorized_keys /root/.ssh/authorized_keys
RUN chmod 0600 /root/.ssh/authorized_keys

CMD /usr/sbin/sshd -D