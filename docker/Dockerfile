FROM debian:stable-20210408
USER root
RUN apt-get -y update && apt-get -y upgrade

# Install Docker inside Docker
RUN useradd peertube_admin; groupadd -g 999 docker; usermod -aG $(cat /etc/group | grep docker: | cut -d: -f3) peertube_admin
RUN apt-get -y install apt-transport-https ca-certificates curl gnupg lsb-release
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
RUN echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
RUN apt-get -y update
RUN apt-get -y install docker-ce docker-ce-cli containerd.io

# Install PeerTube?
RUN MY_EMAIL_ADDRESS=peertube_admin@my.domain.tld MY_DOMAIN=my.domain.tld sh -c "$(curl -fsSL https://raw.github.com/kimsible/install-peertube/master/install.sh)"
USER peertube_admin
