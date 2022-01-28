# Build Steps

The zip consists of two folder. **frontend** and **backend**.

- frontend consists of react application.
- backend contains django application.

## How to run/build

Everything is there to get started. If all you want is to run and test.Follow steps below:

## Prerequisite

Before starting, make sure no container exists already. If you are not sure.Run,

1. `docker container prune`
2. `docker image prune`

Since we added Postgresql and replaced sqlite . We must make `migrations` before attempting to do anything.So, run

1. `docker-compose run backend python manage.py makemigrations`
2. `docker-compose run backend python manage.py migrate`

>if `migrate` command gives you some error. You can stop and remove the container which was created in `makemigrations`
>command, and then you can run `migrate` command again.
>(To do so you can run, `docker ps` to get the container name `docker stop <containerName>` to stop the container and 
>`docker rm <containerName>` to remove the container )

## Steps to run

- Open CMD in the folder(where docker-compose.yml is located)
- To run
  - type `docker-compose -f docker-compose.yml -f docker-compose-dev.yml> up` to run in **development** mode.
  - type `docker-compose -f docker-compose.yml -f docker-compose-prod.yml> up` to run in **production** mode.
- Now you can go to your browser and search `localhost:3000` for **react** and `localhost:8000` for **django**.
- Once you test everything and are satisfied. You can tear everything down with the same command but with `down` instead 
of `up` like
  `docker-compose -f docker-compose.yml -f docker-compose-dev.yml> `**`down`**
  similarly for prod run.
  `docker-compose -f docker-compose.yml -f docker-compose-prod.yml> `**`down`**

>If something isn't working you can always see its log by running
>**`docker logs <containerName>`**
>To get the container name. You can run **`docker ps`**. It will give you the list of all running containers. In our 
>case the containers (if you don't change anything) will be

- django-app
- react-app
- postgresdb

>Note - Your terminal will be blocked after typing command. So, if you want non-blocking terminal add `-d` to the 
>command.  
>`docker-compose -f docker-compose.yml -f docker-compose-prod.yml> up`**`-d`**
