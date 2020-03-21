from codercom/code-server:3.0.1

USER root

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y software-properties-common

RUN add-apt-repository ppa:deadsnakes/ppa
RUN apt-get update
RUN apt-get install -y python3.7

RUN curl https://bootstrap.pypa.io/get-pip.py -o /tmp/get-pip.py
RUN python3.7 /tmp/get-pip.py

USER coder

RUN python3.7 -m pip install --user numpy pandas scikit-learn matplotlib Keras tensorflow jupyter
RUN python3.7 -m pip install --user pylint mypy black

RUN code-server --install-extension ms-python.python@2020.1.58038