FROM ubuntu-base:0.0.1

MAINTAINER bgardella@getoveryourself.com


# Remove the default Nginx configuration file
#RUN rm -v /etc/nginx/nginx.conf
# Copy a configuration file from the current directory
#ADD nginx.conf /etc/nginx/
# Append "daemon off;" to the beginning of the configuration
#RUN echo "daemon off;" >> /etc/nginx/nginx.conf

RUN service mysql start

VOLUME /docker_support
ADD ./wp-config.php /docker_support/wp-config.php

#wordpress
RUN wget http://wordpress.org/latest.tar.gz
RUN tar xzvf latest.tar.gz -C /opt
RUN cp /docker_support/wp-config.php /opt/wordpress/wp-config.php


#configure mysql
RUN mysql -uroot -e "CREATE USER 'wordpress'@'%' IDENTIFIED BY 'wp123456'"
RUN mysql -uroot -e "GRANT ALL PRIVILEGES ON *.* TO 'wordpress'@'%' WITH GRANT OPTION"
RUN mysql -uroot -e "CREATE DATABASE IF NOT EXISTS wordpress;"


# Expose ports
EXPOSE 80

# Set the default command to execute
# when creating a new container
CMD service nginx start
