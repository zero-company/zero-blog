# Lightsail ECR Deployment

Setup `docker-compose.yml`

```
version: '3'
services:
  scheduler:
    image: ${DOCKER_REGISTRY}/pipeline_scheduler
    build:
      context: ../
      dockerfile: ./docker/scheduler/Dockerfile
   startup:
     image: ${DOCKER_REGISTRY}/pipeline_setup
     build:
       context: ../
       dockerfile: ./docker/startup/Dockerfile
```

Authenticate w/ registry

```
eval $(aws ecr get-login-password)
```

Create ecr repository

```
for r in $(grep 'image: \${DOCKER_REGISTRY}' docker-compose.yml | sed -e 's/^.*\///') > do > aws ecr create-repository --repository-name "$r" > done
```

## References

- https://stackoverflow.com/questions/44052999/docker-compose-push-image-to-aws-ecr
- https://bobcares.com/blog/docker-compose-push-to-ecr/
- https://www.baeldung.com/ops/docker-run-multiple-commands
- https://docs.docker.com/config/containers/multi-service_container/
- https://www.golinuxcloud.com/docker-compose-multiple-commands/

## Temp

```
# Setup
FROM node:18-alpine
# https://github.com/nodejs/docker-node/tree/b4117f9333da4138b03a546ec926ef50a31506c3#nodealpine
RUN apk add --no-cache libc6-compat
RUN apk add --no-cache supervisor
RUN apk update
WORKDIR /app
RUN yarn global add turbo
RUN apk add nginx

# Build React apps
COPY . .
RUN yarn install
RUN yarn build

# Move build to nginx
COPY ./apps/boc_queue_terminal/build ./../usr/share/nginx/html
COPY ./apps/boc_queue_admin/build ./../usr/share/nginx/html/admin

# Run
EXPOSE 80
CMD ["/usr/bin/supervisord"]
# CMD ["/bin/sh", "entrypoint.sh"]
```

```
#!/bin/bash

echo 'Combining boc_queue_terminal and boc_queue_admin'
rm -rf build/*
mkdir build
cp -r ./apps/boc_queue_terminal/build/* ./build
mkdir build/admin
cp -r ./apps/boc_queue_admin/build/* ./build/admin

echo 'Moving build to nginx'
mkdir -p ./usr/share/nginx/html
cp -r ./apps/boc_queue_terminal/build/* ./usr/share/nginx/html

echo 'Starting api w/ admin,terminal'
yarn start:api &
nginx -g 'daemon off;'

wait -n
exit $?
```

docker build -t boc_queue:1 .
docker run -p 3001:3001 -p 8080:8080 boc_queue:1
docker run -p 3001:3001 -p 80:80 boc_queue:1

EXPOSE 80
CMD ["/usr/bin/supervisord"]
CMD ["/bin/sh", "entrypoint.sh"]
