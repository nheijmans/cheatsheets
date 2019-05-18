## Cheatsheet: Docker
#### Start a docker container from image in the docker hub
``` docker run -d -p $port:$port -e '$PARAMETERS' $DOCKER/NAME:latest ```

#### List running dockers
``` docker ls ```
``` docker ps ```

#### Copy file from/to container
``` docker cp <container>:/path/to/file.ext . ```
``` docker cp file.ext <container>:/path/to/file.ext ```

#### Resources
``` https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes ```
