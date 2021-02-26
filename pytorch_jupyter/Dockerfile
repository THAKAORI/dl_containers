FROM pytorch/pytorch:latest

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y git
RUN pip install --upgrade pip
RUN pip install jupyterlab
RUN mkdir ./dllearn && cd ./dllearn
RUN pip install -U jupyterlab
RUN pip install numpy scipy pandas matplotlib scikit-image scikit-learn seaborn ipywidgets
RUN pip install IProgress