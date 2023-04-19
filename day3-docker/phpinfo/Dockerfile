FROM ubuntu:22.04
LABEL author="manu"
ARG DEBIAN_FRONTEND=noninteractive
RUN apt update && apt install apache2 -y
RUN apt install php libapache2-mod-php -y
RUN echo "<?php phpinfo() ?>" > /var/www/html/info.php
EXPOSE 80
CMD ["apache2ctl","-D","FOREGROUND"] 



FROM ubuntu:22.04
LABEL author="manu"
ARG DEBIAN_FRONTEND=noninteractive
RUN apt update && apt install nginx -y
RUN apt install php php8.1-fpm -y
RUN echo "<?php phpinfo() ?>" > /var/www/html/info.php
EXPOSE 80
CMD ["nginx","-g","daemon off;"] 

FROM ubuntu:22.04
LABEL author="manu"
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update -y
RUN apt-get upgrade -y
RUN apt-get update && apt install nginx -y
RUN apt-get install php8.1-fpm -y
RUN chmod -R 777 /var/www/html
RUN echo "<?php phpinfo() ?>" >> /var/www/html/info.php
RUN service nginx restart
RUN service php8.1-fpm start
EXPOSE 80
CMD ["nginx","-g","daemon off;"] 


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