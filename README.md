# climahub-docker
This repo contains the docker-compose file to deploy 2 containers for a LAPP stack 
- Linux
- Apache
- PHP7
- PostgreSQL

The webapp container uses a custom made docker image that can be found under php7-apache-pg or directly cloned from docker hub using:  [jmadrazo97/php-pg-apache:latest](https://hub.docker.com/repository/docker/jmadrazo97/php-pg-apache)

To run the containers you can just run: 
```
docker-compose up -d 
```
# Only run apache
If you would like to run the apache container use:
```
docker run -d -p 80:80  -v /home/cloud_user/Desktop/climahub:/app jmadrazo97/php-pg-apache:latest
```
## Apache custom image : php-pg-apache
php-pg-apache image is important becuase this stack needs:
- PHP7
- PHP7XML
- php7.3-pgsql

PHP7 is not directly available to import from ubuntu so ppa:ondrej/php's repo must be imported manually. 

## postgres container
The postgres container uses postgresql image in it's latest version and uses database.env to set database, password and user. 

On both containers is important to take care of the -v or volumes parameter since these lines attach a physical/local folder in order to preserve our data from both postgres and apache.