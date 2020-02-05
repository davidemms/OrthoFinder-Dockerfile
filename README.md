# Orthofinder-Dockerfile
Dockerfile for [davidemms/OrthoFinder](https://github.com/davidemms/OrthoFinder)

Many thanks to Monjeaud Cyril & Roder Thomas for initially developing this dockerfile.

How to use? See https://cloud.docker.com/repository/docker/davidemms/orthofinder/

Current version: 2.3.8

## Building
Docker: `docker build --tag davidemms/orthofinder:<tag> .`

Podman: `podman build --file=Dockerfile --tag=davidemms/orthofinder:<tag> .`

## Run interactively
Docker: `docker run --interactive --tty --rm davidemms/orthofinder:<tag> sh`

Podman: `podman run --interactive --tty --rm davidemms/orthofinder:<tag> sh`

## Run for real
Docker: `docker run --ulimit nofile=1000000:1000000 -it --rm -v /full/path/to/fastas:/input:Z davidemms/orthofinder:<tag> orthofinder -f /input`

Docker, using multiple sequence alignment trees: `docker run --ulimit nofile=1000000:1000000 -it --rm -v /full/path/to/fastas:/input:Z davidemms/orthofinder:<tag> orthofinder -f /input -M msa`

podman: `podman run --ulimit=host                   -it --rm -v /full/path/to/fastas:/input:Z localhost/davidemms/orthofinder:<tag> orthofinder -f /input`

## Push to dockerhub
`docker push davidemms/orthofinder:<tag>`

## Possible error
If the container fails with `IOError: [Errno 24] Too many open files`, ensure the ulimit on the host is high enough (`ulimit -a`) and run the container with this additional option:

Docker: `--ulimit nofile=1000000:1000000`

Podman: `--ulimit=host`

If Sophos is running on the host machine this can slow OrthoFinder down considerably since it often needs to access thousands of files. If you wish to, see the Sophos website for details on turning Sophos off:
<https://community.sophos.com/kb/en-us/133173>
