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
CMD ["nginx","-g","daemon on;"] 