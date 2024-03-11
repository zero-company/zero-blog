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
