# Docker for symfony 5 project

This repo will help you run symfony 5 stack used in the book 

## The stack

- PHP 7.4
- Nginx
- PostgresSql
- Redis
- Rabbitmq
- Mailcatcher


## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. 
You'll find a Dockerfile for php-fpm containing the necessary packages to install to be able to run the examples from the book.
The first time you run docker-compose can take a while to finish because of php dockerfile, it will be the case only the first time.
Inside docker-compose file, containers redis, rabbitmq and mailcatcher are commented, 
so if you need them just uncomment and rerun docker-compose

### Prerequisites

Docker must be installed.


### Installing

Start by creating a directory for your project:
```
mkdir fancy_new_project
```

Inside your newly created directory create a new directory named "src". 
It's needed by docker-compose to be linked with "/var/www" from within nginx container 
which is the server default path to look for our code.

```
mkdir fancy_new_project/src
```

Cloning this repo inside "fancy_new_project" with the following command:

```
cd fancy_new_project
git clone git@github.com:zendyani/docker-for-symfony5.git
```

## Running

Run docker-compose from within "fancy_new_project/docker-for-symfony5" with the following:
```
docker-compose up
```

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments
I was inspired by the last book about symfony 5 writen by Fabian potentier who use docker extensivly but without running php inside a container, instead php is installed locally and from and article from @MartinPham who did a good work automatting running symfony using docker compose, having some issues with the containers used in his article i combined the two sources to create a docker compose organisation that suit me more.

* [Symfony 5: The Fast Track ebook](https://leanpub.com/symfony5-the-fast-track) 
* [Symfony 5 development with Docker](https://dev.to/martinpham/symfony-5-development-with-docker-4hj8)
