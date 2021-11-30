### Introduction

Docker images required for z1n deployment.

### Build images

Execute from root of app repo

For nginx:

```shell
# For edge
docker build -t custom-erpnext-nginx:latest nginx

# For version-12
docker build --build-arg=FRAPPE_BRANCH=version-12 -t custom-erpnext-nginx:v12 nginx

# For version-13
docker build --build-arg=FRAPPE_BRANCH=version-13 -t custom-erpnext-nginx:v13 nginx
```

For worker:

```shell
# For edge
docker build -t custom-erpnext-worker:latest worker

# For version-12
docker build --build-arg=FRAPPE_BRANCH=version-12 -t custom-erpnext-worker:v12 worker

# For version-13
docker build --build-arg=FRAPPE_BRANCH=version-13 -t custom-erpnext-worker:v13 worker
```
