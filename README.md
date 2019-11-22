# Orthofinder-Dockerfile
Dockerfile for [davidemms/OrthoFinder](https://github.com/davidemms/OrthoFinder)

How to use? See https://cloud.docker.com/repository/docker/troder/orthofinder/

Current version: 2.3.7

## Building
Docker: `docker build --tag troder/orthofinder:<tag> .`

Podman: `podman build --file=Dockerfile --tag=troder/orthofinder:<tag> .`

## Run interactively
Docker: `docker run --interactive --tty --rm troder/orthofinder:<tag> sh`

Podman: `podman run --interactive --tty --rm troder/orthofinder:<tag> sh`

## Run for real
Docker: `docker run --ulimit nofile=1000000:1000000 -it --rm -v /path/to/fastas:/input:Z troder/orthofinder:<tag> orthofinder -f /input -t n_cpu_o -a n_cpu_d -S diamond`

podman: `podman run --ulimit=host                   -it --rm -v /path/to/fastas:/input:Z localhost/troder/orthofinder:<tag> orthofinder -f /input -t n_cpu_o -a n_cpu_d -S diamond`

## Push to dockerhub
`docker push troder/orthofinder:<tag>`

## Possible error
If the container fails with `IOError: [Errno 24] Too many open files`, ensure the ulimit on the host is high enough (`ulimit -a`) and run the container with this additional option:

Docker: `--ulimit nofile=1000000:1000000`

Podman: `--ulimit=host`
