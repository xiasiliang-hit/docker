FROM ubuntu

RUN dpkg-divert --local --rename --add /sbin/initctl
#RUN ln -s /bin/true /sbin/initctl
RUN apt-get -y install aptitude

RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list
RUN apt-get update
RUN apt-get upgrade




RUN aptitude -y install mysql-client mysql-server

RUN sed -i -e"s/^bind-address\s*=\s*127.0.0.1/bind-address =0.0.0.0/" /etc/mysql/my.cnf

ADD ./startup.sh /opt/startup.sh

EXPOSE 3306

CMD ["/bin/bash", "/opt/startup.sh"]
