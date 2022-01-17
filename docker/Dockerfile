# Từ source image tạo container
FROM centos:latest

# RUN: exec container command lần lượt 
RUN yum update -y
RUN yum install httpd httpd-tools -y
RUN yum install vim -y
RUN yum install vim -y
RUN yum install epel-release -y
RUN yum install htop -y

# assign folder làm việc chính của container
WORKDIR /var/www/html

# defailt listen port
EXPOSE 80

# ADD: cho file từ host vào folder của docker
ADD ./assets/test.html /var/www/html

# Command cuối = httpd -D FOREGROUND
ENTRYPOINT [ "httpd" ]
CMD [ "-D", "FOREGROUND" ]
