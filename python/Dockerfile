# this file describes how to build tsuru python image
# to run it:
# 1- install docker
# 2- run: $ docker build -t tsuru/python https://raw.github.com/tsuru/basebuilder/master/python/Dockerfile

from	ubuntu:14.04
run	apt-get update
run	apt-get install wget -y --force-yes
run	wget http://github.com/whilgeek/basebuilder/tarball/master -O basebuilder.tar.gz --no-check-certificate
run	mkdir /var/lib/tsuru
run	tar -xvf basebuilder.tar.gz -C /var/lib/tsuru --strip 1
run	cp /var/lib/tsuru/python/deploy /var/lib/tsuru
run	cp /var/lib/tsuru/base/start /var/lib/tsuru
run /var/lib/tsuru/base/replace
run apt-get update && apt-get install -y openssh-server
run mkdir /var/run/sshd
run echo 'root:screencast' | chpasswd
run sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
run /var/lib/tsuru/base/install
