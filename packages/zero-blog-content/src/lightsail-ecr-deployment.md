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

## Temp

```
FROM node:18-alpine AS base

# Build the React apps
FROM base AS builder
# Setup
# https://github.com/nodejs/docker-node/tree/b4117f9333da4138b03a546ec926ef50a31506c3#nodealpine
RUN apk add --no-cache libc6-compat
RUN apk update
WORKDIR /app
RUN yarn global add turbo
COPY . .
RUN yarn install
RUN yarn build:combinecsr --output-logs=none

# Use Nginx as server
FROM nginx:alpine AS server
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 8080

CMD ["/bin/sh", "entrypoint.sh"]
```

```
#!/bin/bash

echo 'Starting api w/ admin,terminal'

yarn start:api &
nginx -g daemon off; &
```
