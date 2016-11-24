# Docker for Magento 2 development process
--------
Simple compose for Magento 2 that contains:

1. PHP 7.0 (PHP-FPM with xDebug:9000)
2. Nginx (latest)
3. Redis (latest)
4. MySQL (latest)

All required libraries are in-box.

### Configuration
Configuration file is located in **config/env.sh** (change it before installation if needed)

### Installation:

1. $ `mkdir web`
2. `git submodule add url_to_your_project_git_repo ./web`. Put your Magento 2 project files into **./web** folder.
3. $ `docker-machine create customvmname --driver virtualbox` **WARNING**: Regular expression for customvmname `/^[a-zA-Z0-9]+[a-zA-Z]$/`. If you use MacOS, then you should use "vmwarefusion" driver, because of VB file permission problems with MacOS volumes.
4. $ `eval $(docker-machine env customvmname)`
5. $ `chmod u+x bin/console`
6. $ `bin/console install yourdomain.local`
7. Process can take up to 30 min
8. $ `docker-machine ip customvmname` (get machine IP)
9. Copy output of step #7 to /etc/hosts as domain you set in step #5
10. Check in browser. Done ;)

### Docker commands
1. To start docker-machine use `docker-machine start yourmvmname`
2. To stop docker-machine use `docker-machine stop yourmvmname`
3. To start compose inside docker-machine use `bin/console start`
4. To stop compose inside docker-machine use `bin/console stop`
5. To restart compose inside docker-machine use `bin/console restart`

### Magento 2 commands
1. To run bin/magento command use `bin/console magento [arguments]` eg. `bin/console magento cache:clean`

### Redis commands
1. To open redis-cli just use `bin/console redis-cli [arguments]` eg. `bin/console redis-cli flushall`

### Logs commands
1. To see (in real time) nginx errors `bin/console nginx-error-logs|nginx-access-logs`. Use `nginx-error-logs` for tailing /var/log/nginx/error.log and `nginx-access-logs` for tailing /var/log/nginx/access.log

This solution is only improvement of @arvatoSCM [project][aSCM].

[aSCM]: <https://github.com/arvatoSCM/dockerize-magento2>