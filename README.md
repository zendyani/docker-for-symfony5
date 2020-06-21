# docker-for-symfony5

# Introduction
This repo os intended for the reader of the book sumfony 5 fast track.
Inside the book you'll find how to use docker to run the project source code but without using docker for php.
The local php install is used, if you have difficult to install php 7.2 and later tricky in your system then this
repo is for you.


# How to start a new sf5 project using docker
- Clone this repo
- Create src/ dir or update configuration inside docker-compose to reflect your directory configuration
Update line 41 "- ../src:/var/www" with what suit you best.
- Inside src/ init your symfony project usinf symfony command or composer
- Run docker-compose up and you're ready to go.


Incase you don't have the right version of php you can run it from within your php container as the following:
docker-compose run php-fpm + your command (composer or other)
```
docker-compose run php-fpm composer require make 
docker


# Note
Php build may take some time to compile the first time you run docker-compose, 
what you need to keep in mind is all the extension needed in the book will be installed