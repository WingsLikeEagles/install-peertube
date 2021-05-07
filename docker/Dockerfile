FROM debian:stable-20210408
USER root
RUN groupadd -g 999 docker; usermod -aG $(cat /etc/group | grep docker: | cut -d: -f3) peertube_admin
RUN curl -sSL https://get.docker.com/ |sh
RUN MY_EMAIL_ADDRESS=peertube_admin@my.domain.tld MY_DOMAIN=my.domain.tld -c "$(curl -fsSL https://raw.github.com/kimsible/install-peertube/master/install.sh)"
USER peertube_admin
