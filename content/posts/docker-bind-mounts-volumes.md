---
title: "Docker Bind Mounts & Volumes"
date: "2024-07-12"
summary: "Difference between bind mounts & volumes in docker."
description: "Difference between bind mounts & volumes in docker."
toc: false
readTime: false
autonumber: false
math: false
tags: ["docker"]
showTags: false
hideBackToTop: false
---
Containers need to share state between runs more often than not. You may also want to share configurations or other source files from your host machine to your running Docker container to "hot-reload" changes as you modify your local files. 
### Bind Mounts
Bind Mounts help you share files or directories from the host machine to the running Docker container. Reading and writing is bidirectional, i.e., you can read/write from both the running container and your host machine.

To use bind mounts, you simply specify your files or directories when you first  run your container.

```
docker run --mount type=bind,source=/path/to/source,target=/path/to/target/in/container image_name 
```

A possible scenario where this might be helpful is when running a web server like NGINX or Caddy container. You mount the html and config files to your container and modify them to see the changes get reflected in the running container.

Learn more here: https://docs.docker.com/storage/bind-mounts/
### Volumes
Volumes help you maintain state between runs of your container. Volumes can also be shared between different container types. While bind mounts are managed by you host machine's file system, volumes are managed by Docker. Thus, you can create and delete volumes independent of your containers.

You can create a volume with the following commands:
```
docker volume create newvol
```

You attach this volume in CLI with this:
```
docker run --mount source=newvol,target=/path/to/target/in/container image_name 
```

or you can specify in your `Dockerfile` for creating an image mounted to a volume:
```Dockerfile
FROM some_base_image
...
VOLUME newvol
...
```

A possible useful scenario for Volumes are for gathering logging data from different running containers.

Learn more about volumes here: https://docs.docker.com/storage/volumes/