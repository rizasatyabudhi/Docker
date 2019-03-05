#Development
* Build Image `docker build -f Dockerfile.dev .`
* Run Container using docker compose `docker-compose up --build`

#Production
* `docker build . -t rizasatyabudhi/frontend`
* `docker run -p 8080:80 rizasatyabudhi/frontend` 80 is the default port for NGINX