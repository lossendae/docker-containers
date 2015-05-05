# Apache + mod-php + PHP5.2.17

```
docker run --privileged=true --name app-apache \
        -v /var/www/site:/var/www/site \
        -v /app/services/apache/sites-enabled:/etc/apache2/sites-enabled \
        -v /app/services/apache/ssl:/services/apache/config/ssl \
        -v /app/services/log/apache:/var/log/apache2 \
        -v /app/services/log/apache:/services/log/apache \
        -p 80:80 \
        -p 443:443 \
        -d lossendae/apache
```

Clean up before if necessary

```
docker stop app-apache && \
docker rm app-apache
```

## Build container

```
docker build -t lossendae/apache .
```

Clean up before if necessary

```
docker stop app-apache && \
docker rm app-apache && \
docker rmi lossendae/apache
```
