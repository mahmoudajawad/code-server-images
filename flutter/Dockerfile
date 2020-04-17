from codercom/code-server:3.1.1

USER root
RUN apt-get update
RUN apt-get install -y unzip

WORKDIR /home/coder
USER coder
RUN git clone https://github.com/flutter/flutter.git
RUN /home/coder/flutter/bin/flutter upgrade
RUN /home/coder/flutter/bin/flutter config --enable-web

USER root
RUN ln -s /home/coder/flutter/bin/flutter /usr/local/bin/flutter
USER coder

WORKDIR /home/coder/project
RUN code-server --install-extension Dart-Code.dart-code
RUN code-server --install-extension Dart-Code.flutter

RUN code-server --install-extension donjayamanne.githistory
RUN code-server --install-extension chiragpat.tomorrow-and-tomorrow-night-operator-mono-theme
RUN code-server --install-extension streetsidesoftware.code-spell-checker