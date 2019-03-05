* Every single container is running inside of linux virtual machine
* Every container is isolated from each other


## SIMPLE COMMAND
* `docker run` = docker start + docker exec
* `docker ps -a`  = shows all running containers
* `docker stop/kill id` = stop a container (stop --> kill)
* `docker system prune` = remove all unused containers, objects, etc
* `docker logs id` = print the output (without rerunning/restarting the container)

#### RUN COMMAND INSIDE DOCKER CONTAINER
* `docker run redis` = run redis
* `docker exec -it id redis-cli` = run redis command
* `docker exec -it id sh` = look into the continer's directory


## BUILD CUSTOM DOCKER IMAGE
* `docker build .` (without tagging)
* `docker build -t rizasatyabudhi/redis:latest .` (with tagging)
* `docker build -f Dockerfile.dev .` (build docker with custom `Dockerfile.dev` name)

* rizasatyabudhi = docker ID
* redis = repo name

* when we first build the docker image with `docker build .`, all the files in our project (`package.json`) is not available yet for that image, so we need to copy and paste it first to the image
`COPY ./ ./`

* We need to specify the `WORKDIR /usr/app` so our files is not copied to the container's root directory

* We need PORT mapping, so our client can access our container's port
`docker run -p 8080:8080 (incoming request from client:port inside container) rizasatyabudhi/simpleweb`


## DOCKER COMPOSE
* Create multiple containers on the same network so they can communicate
* To simplify docker-cli command

* `docker-compose up --build` = build and run the containers (with changes)
* `docker compose up -d` = run the containers
* `docker-compose down` = stop the containers
* `docker-compose ps` = to see all running containers, must be run in a directory that has `docker-compose.yml`

## DOCKER RESTART POLICY
Specify to restart the container if something happened, see the `restart policies`

## DOCKER VOLUME MAPPING
* Use case : Hot reload
* To map the folder inside the container with the folder outside the container (our dev env)
* bookmark the `node_modules` to exclude `node_modules` from mapping, because in our local dev env it is not present
* `docker run -p 3000:3000 -v /app/node_modules -v "$(pwd):/app" image_id`
* Create `docker-compose.yml` file for shorter command, then run `docker-compose up`

## MULTISTEP BUILD PROCESS
* NGINX = used to serve `index.html` & `main.js` file