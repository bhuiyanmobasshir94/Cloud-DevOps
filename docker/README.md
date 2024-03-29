the following steps solved the problem for me.

remove docker:
```
$ sudo apt-get remove docker docker-engine
```
reinstall with
```
curl -sSL https://get.docker.com/ | sh
```
add user to a group:
```
sudo usermod -aG docker $USER
```
The `docker system prune` command removes all stopped containers, dangling images, and unused networks:
```
docker system prune -f
```
If you want to tag a docker image and push to the registry do the following:

```
$ docker image tag rhel-httpd:latest registry-host:5000/myadmin/rhel-httpd:latest
$ docker image push registry-host:5000/myadmin/rhel-httpd:latest
```
```
# List all containers (only IDs)
docker ps -aq
# Stop all running containers
docker stop $(docker ps -aq)
# Remove all containers
docker rm $(docker ps -aq)
# Remove all images
docker rmi $(docker images -q)
```
To find all the containers and stop and remove them:
```
docker ps -a
docker stop <container_id>
docker rm -f <container_id>
```
To find all the images and stop and remove them:
```
docker images
docker stop <image_id>
docker rmi -f <image_id>
```
Docker build command:
```
docker build src -f Dockerfile -t registry.graaho.net/defence/museum-cms
```
Docker image run command:
```
docker run -it --rm -p 8004:8004 --env-file django.env registry.graaho.net/defence/museum-cms:latest
```
To uninstall docker-compose:
```
sudo rm $(which docker-compose)
```
If docker is getting permission issue:
```
sudo gpasswd -a $USER docker
newgrp docker
```
To do bash into the container:
```
docker exec -it <container name> /bin/bash
```
Or you can do the same using `docker-compose`:
```
docker-compose exec api python3 manage.py migrate
docker-compose exec api python3 src/manage.py loaddata --app core group.json user.json
docker-compose exec api python3 manage.py collectstatic
```
To see the log from docker container
```
docker container logs --details container-id
docker logs container-id -f
```
If you are restoring a fresh database from another database, You need to dumpdata like this:
```
./manage.py dumpdata --exclude auth.permission --exclude contenttypes > db.json
```
```
cat data_dump.json | docker-compose exec -T app python manage.py loaddata --format=json -
```
## Resources
1. [How to copy docker images](https://stackoverflow.com/questions/23935141/how-to-copy-docker-images-from-one-host-to-another-without-using-a-repository)
2. [How To Remove Docker Containers, Images, Volumes, and Networks](https://linuxize.com/post/how-to-remove-docker-images-containers-volumes-and-networks/#:~:text=%2D%2Drm%20flag.-,Removing%20one%20or%20more%20containers,containers%20you%20want%20to%20remove.)
3. [docker push](https://docs.docker.com/engine/reference/commandline/push/)
4. [A journey through Django and Docker: hands-on production deployment principles and ideas](https://dev.to/zompro/a-journey-through-django-and-docker-hands-on-production-deployment-principles-and-ideas-17a3)
5. [Dockerizing Django with Postgres, Gunicorn, and Nginx](https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/)
6. [Deploying Django to AWS with Docker and Let's Encrypt](https://testdriven.io/blog/django-docker-https-aws/)
7. [How To Use docker exec to Run Commands in a Docker Container](https://www.digitalocean.com/community/tutorials/how-to-use-docker-exec-to-run-commands-in-a-docker-container)

## Issues
- [Docker fails with OCI runtime create failed](https://dev.to/aheissenberger/docker-fails-with-oci-runtime-create-failed-4e3l)
- [getting-permission-denied-in-docker-run](https://stackoverflow.com/questions/44687685/getting-permission-denied-in-docker-run)
- [standard-init-linux-go178-exec-user-process-caused-exec-format-error](https://stackoverflow.com/questions/42494853/standard-init-linux-go178-exec-user-process-caused-exec-format-error)
- [Multi-arch build and images, the simple way](https://www.docker.com/blog/multi-arch-build-and-images-the-simple-way/)
