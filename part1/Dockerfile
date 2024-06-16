# # Start from the alpine image that is smaller but no fancy tools
# FROM alpine:3.19

# # Use /usr/src/app as our workdir. The following instructions will be executed in this location.
# WORKDIR /usr/src/app

# # Copy the hello.sh file from this directory to /usr/src/app/ creating /usr/src/app/hello.sh
# COPY hello.sh .

# # Execute a command with `/bin/sh -c` prefix.
# RUN touch additional.txt

# # Alternatively, if we skipped chmod earlier, we can add execution permissions during the build.
# RUN chmod +x hello.sh

# # When running docker run the command will be ./hello.sh
# CMD ./hello.sh

# FROM ubuntu:22.04

# WORKDIR /mydir

# RUN apt-get update && apt-get install -y curl python3
# RUN curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o /usr/local/bin/yt-dlp
# RUN chmod a+x /usr/local/bin/yt-dlp

# CMD ["/usr/local/bin/yt-dlp"]

FROM ubuntu:22.04

WORKDIR /mydir

RUN apt-get update && apt-get install -y curl python3
RUN curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o /usr/local/bin/yt-dlp
RUN chmod a+x /usr/local/bin/yt-dlp

ENTRYPOINT ["/usr/local/bin/yt-dlp"]

# define a default argument
CMD ["https://www.youtube.com/watch?v=Aa55RKWZxxI"]