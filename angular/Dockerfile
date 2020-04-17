from codercom/code-server:3.1.1

USER root

RUN apt-get update
RUN apt-get upgrade -y

WORKDIR /tmp
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -

RUN apt-get install -y nodejs

RUN npm install -g @angular/cli

USER coder

RUN code-server --install-extension donjayamanne.githistory
RUN code-server --install-extension chiragpat.tomorrow-and-tomorrow-night-operator-mono-theme
RUN code-server --install-extension streetsidesoftware.code-spell-checker