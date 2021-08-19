FROM ubuntu:latest

LABEL maintainer "Takahiro_Hori"

RUN apt-get update --fix-missing
# RUN apt-get install -y apt-utils && \
#     apt-get install -y software-properties-common vim curl unzip htop openssh-server wget procps
RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd
RUN echo 'root:takahirohori' | chpasswd
RUN echo '\nPermitRootLogin yes' >> /etc/ssh/sshd_config
# RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
RUN apt-get install -y git

RUN pip install jupyterlab
RUN mkdir ./dllearn && cd ./dllearn
RUN pip install -U jupyterlab
RUN pip install numpy scipy pandas matplotlib scikit-image scikit-learn seaborn ipywidgets
RUN pip install IProgress

# ENV NOTVISIBLE "in users profile"
# RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
