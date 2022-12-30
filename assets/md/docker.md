# Docker cheatsheet

### Build and share
- `docker build -t myimage:1.0 .` Build an image from the Dockerfile in the current directory and tag the image
- `docker tag myimage:1.0 myrepo/myimage:2.0` Retag a local image with a new image name and tag
- `docker push myrepo/myimage:2.0` Push an image to a registry

### Manage
- `docker container rm -f $(docker ps -aq)` Delete all running and stopped containers
- `docker container logs --tail 100 web` Print the last 100 lines of a container’s logs
- `docker ps -a | awk '{ print $1,$2 }' | grep centos:7 | awk '{print $1 }' | xargs -I {} docker rm {}` Remove all containners based on docker image name (in this example, centos:7)