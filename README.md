# Symfony 4.0 RESTful API

Please note this project was built just for testing and educational purposes.

## Prerequisites

Download and install Docker: https://www.docker.com/community-edition

Download and install Git (optional): https://git-scm.com/downloads

### Docker schema

This project provides by default the following Docker Containers:
- Nginx on port 8000
- PHP v7.2 FPM on port 9000
- MySQL on port 3306 with:
  - `root` user and `password` password
  - `symfony` user, `symfony` password and `symfony` database
- Redis on port 6379
- Memcached on port 11211

## Download and install

Just download and extract this repository, or clone it through the following command:

```bash
git clone git@github.com:DavidGarciaCat/sf4-rest.git
```

Go to the project's folder:

```bash
cd sf4-rest
```

And create your `.env` file based on `.env.dist`:

```bash
cp .env.dist .env
```

## Useful Docker commands

Start containers on the foreground (you will see a stream of logs for every container running): 

```bash
docker-compose up
```

Start containers in the background:

```bash
docker-compose up -d
```

Stop containers:

```bash
docker-compose stop
```

List containers:

```bash
docker-compose ps
```

Execute command inside of container:

```bash
docker exec [FLAGS] CONTAINER_NAME COMMAND
```

...where COMMAND is whatever you want to run. Examples:

| Description                   | Command                                      |
| ----------------------------- | -------------------------------------------- |
| Shell into the PHP Container  | docker exec -it sf4-rest-php bash            |
| Install composer dependencies | docker exec sf4-rest-php composer install -o |

Docker provides a single command that will clean up any resources — images, containers, volumes, and networks — that are dangling (not associated with a container):

```bash
docker system prune
```

To additionally remove any stopped containers and all unused images (not just dangling images), add the -a flag to the command:

```bash
docker system prune -a
```

## How to access to the API endpoints

Just browse your Local Host targeting port 8000: http://localhost:8000/

## Thanks

This repository has been created just for testing and educational purposes, based on these 2 examples:
- https://gist.github.com/michaelneu/2ca7987ef00fa3fbe4fd7b9c07834cc7
- https://github.com/maxpou/docker-symfony
