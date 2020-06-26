# base image: last debian release
FROM debian:buster


###############################################################################
# system configuration (packages, user account) + unpack etherpad-lite
###############################################################################

# get the latest package lists and apply the needed upgrades
RUN apt-get update && apt-get -y dist-upgrade


# TODO: install required packages
RUN apt-get -y install --no-install-recommends npm gzip git curl python libssl-dev pkg-config build-essential unzip
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get install -y nodejs

# create a dedicated user
RUN useradd --create-home etherpad

# get the sources of etherpad-lite
# https://github.com/ether/etherpad-lite/releases/latest
#ADD https://codeload.github.com/ether/etherpad-lite/tar.gz/1.6.1   /tmp/source.zip
COPY 1.6.1.zip   /tmp/src.zip

# TODO

RUN unzip -q /tmp/src.zip  -d /opt/
#RUN unzip /tmp/src.zip  -d /opt/etherpad
RUN mv /opt/ether-etherpad-lite-9f51432 opt/etherpad/
#RUN mv /tmp/etherpad/ether-etherpad-lite-9f51432/ opt/etherpad/
#RUN rm /tmp/src.zip
RUN chown -R etherpad /opt/etherpad/
RUN chown -R etherpad /var/
STOPSIGNAL SIGINT
#USER etherpad
WORKDIR /opt/etherpad
RUN ./bin/installDeps.sh
HEALTHCHECK --interval=5m --timeout=3s CMD curl -f http://127.0.0.1:9001/ || exit 1
EXPOSE 9001/tcp
VOLUME ["var/"]
#VOLUME ["/opt/etherpad/var/"]
RUN ln -s SESSIONKEY.txt ./var/SESSIONKEY.txt
CMD ["./bin/run.sh", "--root"]


