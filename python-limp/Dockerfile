from codercom/code-server:3.1.1

USER root

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y software-properties-common build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev wget libcairo2 libpango-1.0-0 libpangocairo-1.0-0 libgdk-pixbuf2.0-0 libffi-dev shared-mime-info
WORKDIR /tmp
RUN wget https://www.python.org/ftp/python/3.8.1/Python-3.8.1.tgz
RUN tar -xf Python-3.8.1.tgz
WORKDIR /tmp/Python-3.8.1
RUN ./configure --enable-optimizations
RUN make -j 8
RUN make altinstall

RUN apt-get install -y mongodb

USER coder

RUN python3.8 -m pip install --user -r https://raw.githubusercontent.com/masaar/limp/master/requirements.txt
RUN python3.8 -m pip install --user pylint mypy black

RUN code-server --install-extension ms-python.python
RUN code-server --install-extension donjayamanne.githistory
RUN code-server --install-extension chiragpat.tomorrow-and-tomorrow-night-operator-mono-theme