# Submition
https://linux.die.net/man/1/script

`script -a <file name>#to start record`

`exit #exit`

`col -b < output.txt > clean_output.txt # clean up output` for example `col -b < Exercise_1.2.txt > cleaned.txt`


# Part1 note
| Command                     | Explain                                       | Shorthand     |
|-----------------------------|-----------------------------------------------|---------------|
| `docker image ls`           | Lists all images                              | `docker images` |
| `docker image rm <image>`   | Removes an image                              | `docker rmi`  |
| `docker image pull <image>` | Pulls image from a docker registry, without running them           | `docker pull` |
| `docker container ls -a`    | Lists all containers                          | `docker ps -a`|
| `docker container run <image>` | Runs a container from an image             | `docker run`  |
| `docker container rm <container>` | Removes a container                   | `docker rm`   |
| `docker container stop <container>` | Stops a container                    | `docker stop` |
| `docker container start <container>` | Starts a container                    |`docker start`|
| `docker container rm --force < container>` | =`docker container rm <container>` + `docker container stop <container>` | `docker rm -f`|
| `docker container prune` | Delete all stopped containers | |
| `docker image prune` | Delete all stopped images | |
| `docker run -d <container>` | Starts a container detached. Run it in the background| |
| `docker run -t <container>` | =t will create tty, which is a teletypewriter, can be the terminal interface for input and output | |
| `docker run -it <contrainer>` | -i flag instruct to pass the STDIN (standard input) to the container| |
| `docker ps -a` | Container process status | |
| `docker rm $(docker ps -a -q) -f`| remove all containers||
| `docker rmi $(docker image ls -q) -f` | remove all images||
| `docker logs -f <container>`| Follow the of the ouput of logs||
| `docker pause <container>`| Pause log's output| |
| `docker unpause <container>`| Unpause log's output| |
| `docker attach <container>` | Keep logs open and attach to the running container||
| `docker attach --no-srdin <container>` | Keep logs open and not attach STDIN ||
| `docker container exec <container>` | Executes a command inside the container | `docker exec` |
| `docker exec -it looper bash`| execute the Bash shell in the container in interactive mode| |
## Commands

`docker run -d -it --name looper ubuntu sh -c 'while true; do date; sleep 1; done'`, -c refer to command

`docker run -d --rm -it --name looper-it ubuntu sh -c 'while true; do date; sleep 1; done`, --rm ensures that there are no garbage containers left behind when exited from the container. It alse means `docker start` can not be used to start the container after it has exited.


