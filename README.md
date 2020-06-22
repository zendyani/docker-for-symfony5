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

Create .env file inside docker-for-symfony5 with the following content:
```
DATABASE_NAME=symfony
DATABASE_USER=appuser
DATABASE_PASSWORD=apppassword
DATABASE_ROOT_PASSWORD=secret

APP_ENV=dev
APP_SECRET=24e17c47430bd2044a61c131c1cf6990
```

Those variables will be used to configure postgresql and later symfony, 
So sont hesitate to update variables value accordingly.

## Running

Run docker-compose from within "fancy_new_project/docker-for-symfony5" with the following:
```
docker-compose up
```

To confirm that your containers are running, from another terminal run the following command:
```
docker-compose ps
```

If the result is the listing of tree containers then congratulation you can jump to next step. 

## Init Symfony project
To do so we need to execute php composer commands or symfony command from within php-fpm container.
We have more than one way of doing it.

```
docker-compose run php-fpm composer create-project symfony/skeleton .
```

If everyting goes well, your "src/" folder will contain the generated source code.

## Testing
Open your browser to http://127.0.0.1:8080/ 
If wil get a webpage with the message "Welcome to Symfony 5.1.2"

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments
I was inspired by the last book about symfony 5 writen by Fabian potentier who use docker extensivly but without running php inside a container, instead php is installed locally and from and article from @MartinPham who did a good work automatting running symfony using docker compose, having some issues with the containers used in his article i combined the two sources to create a docker compose organisation that suit me more.

* [Symfony 5: The Fast Track ebook](https://leanpub.com/symfony5-the-fast-track) 
* [Symfony 5 development with Docker](https://dev.to/martinpham/symfony-5-development-with-docker-4hj8)
