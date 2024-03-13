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

## Temp

```
# Setup
FROM node:18-alpine
# https://github.com/nodejs/docker-node/tree/b4117f9333da4138b03a546ec926ef50a31506c3#nodealpine
RUN apk add --no-cache libc6-compat
RUN apk update
WORKDIR /app
RUN yarn global add turbo
RUN apk add nginx
RUN systemctl start nginx

# Build React apps
COPY . .
RUN yarn install
RUN yarn build
# COPY /app/build /usr/share/nginx/html

# Run
EXPOSE 8080
CMD ["/bin/sh", "entrypoint.sh"]
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
```

docker build -t boc_queue:1 .
docker run -p 3001:3001 -p 8080:8080 boc_queue:1
