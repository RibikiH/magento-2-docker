# Install Step by step

## Install docker

https://docs.docker.com/get-docker/

## Command

``` bash
docker-compose up -d
docker exec -it php_magento /bin/bash

cd /var/www
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data .
chmod u+x bin/magento

bin/magento setup:install \
--base-url=http://localhost:8080 \
--db-host=mysql_magento \
--db-name=database \
--db-user=docker \
--db-password=docker \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--elasticsearch-host=elasticsearch \
--backend-frontname=admin
```