# Lightsail Deployment

Download and move generated ssh key upon instance creation to `C:\Users\yourusername\.ssh`.
Default password can be found in `home/bitnami/bitnami_application_password`

- SSH Connect

```
ssh -i test-project-dev-lightsail.pem bitnami@111.222.333.444
chmod 600 test-project-dev-lightsail.pem
```

you can also open ssh connection remotely on the browser via aws console

Install VS Code extension, VS Code Remote - SSH(ms-vscode-remote.remote-ssh)
Ctrl+Shift+P > Remote-SSH: Connect to Host... > Configure SSH Hosts... > `C:\Users\yourusername\.ssh\config` then add below line...

```
  Host 111.222.333.444
  HostName 111.222.333.444
  IdentityFile "C:\Users\yourusername\.ssh\test-project-dev-lightsail.pem"
  User bitnami
```

- Update

```
sudo apt-get update
```

- Git

To clone private github repo inside lightsail, generate ssh key which can be found in `home/bitnami/.ssh/id_rsa.pub`, Add to private github repo deploy keys.

```
ssh-keygen -o -t rsa -C "jigzpalillo@gmail.com"
git clone git@github.com:my-org/my-repo.git
```

- MongoDB

Setup

```
mongosh admin --username root -p # bitnami_application_password
db.createUser({user: "api", pwd: "", roles: ["userAdminAnyDatabase"]})
db.grantRolesToUser("api", [{ role: "userAdminAnyDatabase", db:"admin" }, "readWriteAnyDatabase"])
show users
db.system.users.find()

use test_project_dev_mongodb
db.config.insertOne( { initialDate: new Date() } )
show dbs, show collections
exit
```

Port forwarding for Compass

```
ssh -i test-project-dev-lightsail.pem -N -f -L 3801:localhost:27017 bitnami@13.210.182.8
```

- PM2

```
sudo yarn global add pm2
pm2 start "yarn start" --name boc_queue
pm2 stop
pm2 ls
pm2 monit
```
