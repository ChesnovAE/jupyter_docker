FROM ubuntu:xenial-20180417

RUN apt-get update \ 
    && apt-get -y install python3-pip \
    && apt-get -y install htop \
    && apt-get -y install tmux

RUN mkdir -p /geo_app/notebooks

RUN pip3 install --upgrade pip \
    && pip3 install --upgrade setuptools

WORKDIR /geo_app

COPY run.sh ./
COPY requirements.txt ./
COPY jupyter_notebook_config.py ./

RUN pip3 install -r requirements.txt

COPY notebooks/ /geo_app/notebooks

CMD [ "/bin/bash", "run.sh" ]