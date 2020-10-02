FROM ubuntu:xenial-20180417

RUN apt-get update
RUN apt-get -y install python3-pip
RUN apt-get -y install htop

RUN mkdir -p /notebooks

RUN pip3 install --upgrade pip
RUN pip3 install --upgrade setuptools
COPY ./requirements.txt /notebooks/requirements.txt
RUN pip3 install -r /notebooks/requirements.txt

COPY ./ /notebooks

WORKDIR /notebooks