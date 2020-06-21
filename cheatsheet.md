# Starting
- docker-compose up
- push docker config for posgres and the one for mysql (to be used for other project)
- connect inside php container
- execute symfony command



# Docker

## Execute command like composer inside docker
docker-compose run php-fpm + your command (composer or other)
```
docker-compose run php-fpm composer require make 
docker-compose run php-fpm php bin/console
```

Or execute 
```
docker-compose exec php-fpm sh
```
And from there you will be able to execute command as if you are inside container

# Reset container
start by removing data files
```
sudo rm -rf database/data/*
```
Rebuild containers
```
docker-compose up --build
```