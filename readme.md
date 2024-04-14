# Submition
https://linux.die.net/man/1/script
`script -a <file name>#to start record`
`exit #exit`
`col -b < output.txt > clean_output.txt # clean up output` for example `col -b < Exercise_1.2.txt > cleaned.txt`

# Note
| Command                     | Explain                                       | Shorthand     |
|-----------------------------|-----------------------------------------------|---------------|
| `docker image ls`           | Lists all images                              | `docker images` |
| `docker image rm <image>`   | Removes an image                              | `docker rmi`  |
| `docker image pull <image>` | Pulls image from a docker registry, without running them           | `docker pull` |
| `docker container ls -a`    | Lists all containers                          | `docker ps -a`|
| `docker container run <image>` | Runs a container from an image             | `docker run`  |
| `docker container rm <container>` | Removes a container                   | `docker rm`   |
| `docker container stop <container>` | Stops a container                    | `docker stop` |
| `docker container rm --force < container>` | =`docker container rm <container>` + `docker container stop <container>` | `docker rm -f`|
| `docker container exec <container>` | Executes a command inside the container | `docker exec` |
| `docker container prune` | Delete all stopped containers | |
| `docker image prune` | Delete all stopped images | |
| `docker run -d <container>` | Starts a container detached. Run it in the background| |
| `docker ps -a` | Container process status | |
| `docker rm $(docker ps -a -q) -f`| remove all containers||
| `docker rmi $(docker image ls -q) -f` | remove all images||