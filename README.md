# dev-image-server
Incredibly simple NGINX static image server in a docker container.

## About

When I'm doing front-end work - particularly when I'm doing tedious CSS layouts for images - I like to rotate through a set of placeholder images rather than use a single placeholder image; I get bored quickly if I'm looking at the same image for too long, so this keeps me engaged. I have a directory of my favorite placeholder images on my computer, and usually I use [json-server](https://github.com/typicode/json-server) to serve them all on a simple static file server. Then, on my client, I will spin up a simple function that returns a random image from my server.

I need more practice with docker and NGINX, so I decided to create my own version of this server as a docker container.

### Mounting Images Directory

I think normally - if you only had a few images - you would just put the images directory in the docker image, but my image directory has 2000 jpegs in it. I don't know for sure, but my gut tells me that sticking 2000 jpegs in a docker image is not a good idea.

Docker has what they call a [bind mount](https://docs.docker.com/storage/bind-mounts/), which allows you to mount a directory outside of the docker container from within the docker container. I have included a run command to do this with the sample images directory in this project.

## Instructions

> NOTE: You must have docker engine installed for these commands to work

**To build:**

```bash
# from root directory
docker build -t devimageserver nginx

# see here for more options:
# https://docs.docker.com/engine/reference/commandline/build/
```

**To run:**

with bind mount to project images directory:

```bash
# from root directory
docker run -d --name devimageserver \
--mount type=bind,source="$(pwd)"/images,target=/usr/share/nginx/images,readonly \
-p 8080:80 devimageserver

# serve on localhost:8080

# more options:
# https://docs.docker.com/engine/reference/commandline/run/
```



---

### *References*

1.  [NGINX - Deploying NGINX and NGINX Plus on Docker](https://docs.nginx.com/nginx/admin-guide/installing-nginx/installing-nginx-docker/)
