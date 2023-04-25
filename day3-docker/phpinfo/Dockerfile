FROM ubuntu:22.04
LABEL author="manu"
ARG DEBIAN_FRONTEND=noninteractive
RUN apt update && apt install apache2 -y
RUN apt install php libapache2-mod-php -y
RUN echo "<?php phpinfo() ?>" >> /var/www/html/info.php
EXPOSE 80
CMD ["apache2ctl","-D","FOREGROUND"] 



FROM ubuntu:22.04
LABEL author="manu"
ARG DEBIAN_FRONTEND=noninteractive
RUN apt update && apt install nginx -y
COPY nginx.conf /etc/nginx/nginx.conf
RUN service nginx restart
RUN add-apt-repository ppa:ondrej/php -y
RUN apt update
RUN apt install php8.0-fpm php8.0-common -y
RUN echo "<?php phpinfo() ?>" >> /var/www/html/info.php
EXPOSE 80
ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["nginx","-g","daemon off;"] 

FROM ubuntu:22.04
LABEL author="manu"
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update -y
RUN apt-get upgrade -y
RUN apt-get update && apt install nginx -y
RUN  echo "<?php phpinfo(); ?>" >> /etc/nginx/nginx.conf
RUN apt-get install php8.1-fpm -y
RUN chmod -R 777 /var/www/html
RUN echo "<?php phpinfo(); ?>" >> /var/www/html/info.php
RUN service nginx restart
RUN service php8.1-fpm start
EXPOSE 80
CMD ["nginx","-g","daemon off;"] 
``
## final for nginx
FROM ubuntu:22.04
LABEL author="manu"
ARG DEBIAN_FRONTEND=noninteractive
RUN apt update && apt upgrade -y
RUN apt install nginx -y
RUN apt install php8.1 php8.1-fpm -y && \
    rm -rf /var/lib/apt/lists/
COPY nginx.conf /etc/nginx/sites-available/default
RUN nginx -t
RUN chmod -R 777 /var/www/html
RUN echo "<?php phpinfo() ?>" >> /var/www/html/info.php
RUN service php8.1-fpm restart
EXPOSE 80
ENTRYPOINT ["/bin/bash","-c","service php8.1-fpm start && nginx -g 'daemon off;'"]
CMD ["nginx","-g","daemon off;"]
```


/etc/nginx/sites-available/default

sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install nginx -y
sudo systemctl status nginx
sudo apt-get install php8.1-fpm -y
sudo systemctl status php8.1-fpm
sudo nano /etc/nginx/sites-available/default
sudo nginx -t
sudo systemctl restart nginx
sudo chmod -R 777 /var/www/html
echo "<?php phpinfo(); ?>" >> /var/www/html/info.php