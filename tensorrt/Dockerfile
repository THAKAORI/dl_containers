FROM nvcr.io/nvidia/tensorrt:21.05-py3

LABEL maintainer "Takahiro_Hori"

RUN /opt/tensorrt/python/python_setup.sh
RUN /opt/tensorrt/install_opensource.sh

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update --fix-missing
RUN apt-get install -y git
RUN apt-get install -y apt-utils && \
    apt-get install -y software-properties-common vim curl unzip htop openssh-server wget procps
RUN mkdir /var/run/sshd
RUN echo 'root:takahirohori' | chpasswd
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

RUN pip install jupyterlab

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
