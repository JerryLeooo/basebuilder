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
run mkdir $HOME/.pip
run echo '[global]' >> $HOME/.pip/pip.conf
run echo 'index-url = http://pypi.iguokr.com/guokr/dev/+simple' >> $HOME/.pip/pip.conf
run echo '[install]' >> $HOME/.pip/pip.conf
run echo 'use-mirrors = true' >> $HOME/.pip/pip.conf
run echo 'mirrors = http://pypi.iguokr.com/' >> $HOME/.pip/pip.conf
run echo '[easy_install]' >> $HOME/.pydistutils.cfg
run echo 'index_url = http://pypi.iguokr.com/guokr/dev/+simple' >> $HOME/.pydistutils.cfg
run	/var/lib/tsuru/base/install