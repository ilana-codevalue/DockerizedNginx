# Docker excersize #1
1 weapp
6 mysql db replicas
weapp image pulled from local registry in external container outside the compose file 

1. Clone WebApp from GitHub repository - i didn't clone, i used index.html to be served by nginx.
2. Create Dockerfile using Nginx Image and copy WebApp
3. Build Docker image via Dockerfile.
4. Save this image to be used later.
5. Add db mysql container from https://hub.docker.com/_/mysql
6. add mysql to your docker-compose
7. Running the docker-compose up, make sure all service are up, make sure your can ping between services.
8. exec to one of the services and ping to the other:
    find web container ip address: docker inspect dockerexc1_web_1
    find mysql 1st container ip: docker inspect dockerexc1_db_1
    get into container bash shell: docker exec -ti dockerexc1_web_1 bash
    ping to db container: ping ..

9. docker compose use environment variables from a file.
10. docker compose persistent volume.
11. Docker compose service replicas.

steps 1-11 covered by compose file: docker-compose up -d

12. Create local registry, docker save & docker load & docker tag & docker push to local registry.

create local registry in ceperate container: docker run -d -p 5000:5000 --name registry -v /registry:/var/lib/registry registry:2
tagging the webapp image: docker tag dockerexc1_web localhost:5000/my-web
push webapp image to local registry: docker push localhost:5000/my-web
pulling webapp image done by setting: image: localhost:5000/my-web:latest in the compose file




