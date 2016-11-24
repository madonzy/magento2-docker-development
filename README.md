# Docker for Magento 2 development process
--------
Simple compose for Magento 2 that contains:
1. PHP 7.0 (PHP-FPM with xDebug)
2. Nginx (latest)
3. Redis (latest)
4. MySQL (latest)

All required libraries are in-box.

### Configuration
Configuration file is located in **config/env.sh** (change it before installation if needed)

### Installation:

1. Put latest varsion of Magento (or your project files) into **./web** folder.
2. Remove file web/.gitkeep (optional)
3. $ docker-machine create name_of_vm --driver virtualbox
If you use MacOS, then you should use "vmwarefusion" driver, because of VB file permission problems with MacOs volumes.
4. $ `eval $(docker-machine env name_of_vm)`
5. $ `bin/console install yourdomain.local`
6. Process can take up to 30 min
7. $ `docker-machine ip name_of_vm` (get machine IP)
8. Copy output of step #7 to /etc/hosts as domain you set in step #5
9. Check in browser. Done ;)

### Usefull commands
To start docker-machine use `bin/console start`
To stop docker-machine use `bin/console stop` (VM doesn't stops, only containers are turn off)
To restart docker-machine use `bin/console restart`
To run bin/magento command use `bin/console exec [arguments]` eg. `bin/console exec cache:clean`

This solution is only modification and stuctural separation of @arvatoSCM [project][aSCM].

[aSCM]: <https://github.com/arvatoSCM/dockerize-magento2>