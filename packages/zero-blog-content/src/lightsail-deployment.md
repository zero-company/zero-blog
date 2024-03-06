# Lightsail Deployment

Download and move generated ssh key upon instance creation to `C:\Users\yourusername\.ssh`.

- SSH Connect

```
ssh -i test-project-dev-lightsail.pem bitnami@111.222.333.444
chmod 600 test-project-dev-lightsail.pem
```

you can also open ssh connection remotely on the browser via aws console

- Update

```
sudo apt-get update
```

- MongoDB

```
ssh -i test-project-dev-lightsail.pem -N -f -L 3801:localhost:27017 bitnami@13.210.182.8
```
