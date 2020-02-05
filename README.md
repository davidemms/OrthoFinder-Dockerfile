# Orthofinder-Dockerfile
Dockerfile for [davidemms/OrthoFinder](https://github.com/davidemms/OrthoFinder)

Many thanks to Monjeaud Cyril & Roder Thomas for initially developing this dockerfile.

## Running OrthoFinder for real
Using default options: 

`docker run --ulimit nofile=1000000:1000000 -it --rm -v /full/path/to/fastas:/input:Z davidemms/orthofinder orthofinder -f /input`

Print the help file to see all options:

`docker run -it --rm davidemms/orthofinder orthofinder -h`


Docker, using multiple sequence alignment trees: 

`docker run --ulimit nofile=1000000:1000000 -it --rm -v /full/path/to/fastas:/input:Z davidemms/orthofinder orthofinder -f /input -M msa`


## Possible errors
If the container fails with `IOError: [Errno 24] Too many open files`, ensure the ulimit on the host is high enough (`ulimit -a`) and run the container with this additional option:

Docker: `--ulimit nofile=1000000:1000000`

Podman: `--ulimit=host`

If Sophos is running on the host machine this can slow OrthoFinder down considerably since it often needs to access thousands of files. If you wish to, see the Sophos website for details on turning Sophos off:
<https://community.sophos.com/kb/en-us/133173>
