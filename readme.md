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
|`docker container ls -a --last 3`| List last 3 runs| |
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
| `docker search <container>:<tag>`| search image | |
| `docker build . -t <tag>` or `docker build . -t <tag>`| Need a `Dockerfile` in path `.`,  docker build with instructions where to build (`.`) and give it a name (`-t <name>`) -t refer to tag| |
| `docker diff <container_name>`| The character in front of the file name indicates the type of the change in the container's filesystem: A = added, D = deleted, C = changed. ls can create .ash_history | |
| `docker commit <container_name> <new_image_name>`| save the changes as a new image | |
|`docker run -p <host-port>:<container-port>`| Publish a port. We could also limit connections to a certain protocol only, e.g. UDP by adding the protocol at the end: `EXPOSE <port>/udp` and `-p <host-port>:<container-port>/udp`. | |




## Commands

`docker run -d -it --name looper ubuntu sh -c 'while true; do date; sleep 1; done'`, -c refer to command，sh is unix shell

`docker run -d --rm -it --name looper-it ubuntu sh -c 'while true; do date; sleep 1; done`, --rm ensures that there are no garbage containers left behind when exited from the container. It also means `docker start` can not be used to start the container after it has exited.

`docker run -v "$(pwd):/mydir" yt-dlp https://www.youtube.com/watch?v=DptFY_MszQs`, `-v` refer to volume. with `-v` option, that requires an absolute path. We mount our current folder as `/mydir` in our container, overwriting everything that we have put in that folder in our Dockerfile.



## Docker file
```
# Start from the alpine image that is smaller but no fancy tools
FROM alpine:3.19

# Use /usr/src/app as our workdir. The following instructions will be executed in this location.
WORKDIR /usr/src/app

# Copy the hello.sh file from this directory to /usr/src/app/ creating /usr/src/app/hello.sh
COPY hello.sh .

# Alternatively, if we skipped chmod earlier, we can add execution permissions during the build.
# RUN chmod +x hello.sh

# When running docker run the command will be ./hello.sh
CMD ./hello.sh # CMD is executed when we call docker run, unless we overwrite it.

```
```
FROM ubuntu:22.04

WORKDIR /mydir

RUN apt-get update && apt-get install -y curl python3
RUN curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o /usr/local/bin/yt-dlp
RUN chmod a+x /usr/local/bin/yt-dlp

# Replacing CMD with ENTRYPOINT
ENTRYPOINT ["/usr/local/bin/yt-dlp"]
```
	`CMD`：提供默认命令和参数，可以被 docker run 命令行参数覆盖。
	`ENTRYPOINT`：配置容器启动时始终运行的命令，不会被 docker run 命令行参数覆盖，但可以与命令行参数组合使用。
    By default, the `ENTRYPOINT` in Docker is set as `/bin/sh -c` and this is passed if no entrypoint is set. `ENTRYPOINT` is giving the file as a parameter to /bin/sh -c

```
FROM ubuntu:22.04

WORKDIR /mydir

RUN apt-get update && apt-get install -y curl python3
RUN curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o /usr/local/bin/yt-dlp
RUN chmod a+x /usr/local/bin/yt-dlp

ENTRYPOINT ["/usr/local/bin/yt-dlp"]
EXPOSE <port> # with docker run -p <host-port>:<container-port> to publish a port

# define a default argument
CMD ["https://www.youtube.com/watch?v=Aa55RKWZxxI"]
```
Now (after building again) the image can be run without arguments to download the video defined in CMD:
However, the argument defined by CMD can be overridden by giving one in the command line:

## External connections into containers
Opening a connection from the outside world to a Docker container happens in two steps:

`Exposing port`: Exposing a container port means telling Docker that the container listens to a certain 

`Publishing port`: Publishing a port means that Docker will map host ports to the container ports



# Part2

