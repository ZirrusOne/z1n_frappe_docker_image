### Introduction

Docker images required for z1n deployment.

### Build images

Execute from root of app repo

For nginx:

```shell
# For edge
docker build -t z1n-erpnext-nginx:latest nginx

```

For worker:

```shell
# For edge
docker build -t z1n-erpnext-worker:latest worker

```
