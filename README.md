# jumanpp-docker

[Github](https://github.com/meokz/jumanpp-docker) / [DockerHub](https://hub.docker.com/repository/docker/meokz/jumanpp)

## Usage

* As docker container
```sh
$ docker run -it meokz/jumanpp jumanpp
```

* As builder for multi stage build

```Dockerfile
FROM meokz/jumanpp as jumanpp
FROM debian:buster-slim
COPY --from=jumanpp /usr/local/bin /usr/local/bin
COPY --from=jumanpp /usr/local/libexec /usr/local/libexec
```
