# Docker with GPU
## Setup
`sudo systemctl restart docker`
### Install docker-ce
### Install nvidia-docker
[nvidia-docker](https://github.com/NVIDIA/nvidia-docker)

## Images
### check images
`sudo docker images`
### Pull image
[docker hub](https://hub.docker.com), [pyTorch](https://hub.docker.com/r/pytorch/pytorch/tags)  
`docker pull <repo:version>`, such as `docker pull pytorch/pytorch:latest`  
## Container
### Create container from image
with gpu, mount folder
`sudo docker run -it -d --gpus all --mount type=bind,source=<source folder>,destination=<dest> <image id>`  
e.g.  
`sudo docker run -it -d --gpus all --mount type=bind,source=/home/vivian/git,destination=/repo 83d5fed9611f`
### Attach container
`sudo docker container ls`  
`sudo docker attach <container id>`
### Detach
`Ctrl-p + Ctrl-q`
### Kill container
`exit` bash