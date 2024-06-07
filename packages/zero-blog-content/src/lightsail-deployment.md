# Lightsail Deployment

Download and move generated ssh key upon instance creation to `C:\Users\yourusername\.ssh`.
Default password can be found in `home/bitnami/bitnami_application_password`

## SSH Connect

```
ssh -i boc-queue-dev-lightsail.pem bitnami@3.26.63.139
ssh -i boc-queue-dev-lightsail.pem bitnami@13.210.182.8
ssh -i test-project-dev-lightsail.pem bitnami@111.222.333.444
chmod 600 test-project-dev-lightsail.pem
exit
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

## Update

```
sudo apt-get update
node -v
which node, /opt/bitnami/node/bin/node


```

## Git

To clone private github repo inside lightsail, generate ssh key which can be found in `home/bitnami/.ssh/id_rsa.pub`, Add to private github repo deploy keys.

```
ssh-keygen -o -t rsa -C "jigzpalillo@gmail.com"
git clone git@github.com:my-org/my-repo.git
```

## api

clone project/s to `/home/bitnami`

```
yarn install
screen -S api
yarn start:api
```

- envs

```
cp ./packages/envs/.env.boc_queue_dev_api apps/boc_queue_api/.env
cp ./packages/envs/.env.boc_queue_dev_admin apps/boc_queue_admin/.env
cp ./packages/envs/.env.boc_queue_dev_terminal apps/boc_queue_terminal/.env
```

```
MONGODB_URI= "mongodb://0.0.0.0:27017" # Must not be localhost
MONGODB_DATABASE= "boc_queue_mongodb_local"
MONGODB_USER= "admin"
MONGODB_PASS= "admin"
PORT= "3001"
```

## MongoDB

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

### Port forwarding for Compass

```
ssh -i boc-queue-dev-lightsail.pem -N -f -L 3801:localhost:27017 bitnami@3.26.63.139
ssh -i test-project-dev-lightsail.pem -N -f -L 3801:localhost:27017 bitnami@13.210.182.8
ssh -i boc-queue-dev-lightsail.pem -N -f -L 3801:localhost:27017 bitnami@13.210.182.8
```

- close

https://serverfault.com/questions/1105680/close-kill-a-ssh-local-port-forwarding-connection-no-controlpath-specified-for

```
lsof -i tcp:[PORT]
netstat -bno 3801
netstat -aof | findstr :3801
```

## PM2

```
sudo yarn global add pm2
pm2 start "yarn start" --name boc_queue
pm2 stop
pm2 ls
pm2 monit
```

## Install Docker Compose

```
sudo apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg2 \
    software-properties-common

curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
```

## nginx

```
uname -a
sudo apt update
sudo apt install nginx
sudo apt-get purge nginx nginx-common
sudo apt-get autoremove
```

## lightsail

networking firewall
Custom TCP 3001

- serve

```
yarn global add serve
yarn serve -p 3002 -s build
yarn serve -p 3003 -s build.admin
```

- apache

`sudo /opt/bitnami/ctlscript.sh restart apache`

`opt/bitnami/apache/conf/bitnami/bitnami.conf`

```
<VirtualHost _default_:80>
  DocumentRoot "/opt/bitnami/apache/htdocs"
  <Directory "/opt/bitnami/apache/htdocs">
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted

    RewriteEngine On
    # Don't rewrite files or directories
    RewriteCond %{REQUEST_FILENAME} -f [OR]
    RewriteCond %{REQUEST_FILENAME} -d
    RewriteRule ^ - [L]
    # Rewrite everything else to index.html to allow html5 state links
    RewriteRule ^ index.html [L]
  </Directory>

  # Error Documents
  ErrorDocument 503 /503.html
</VirtualHost>
```

sudo service apache2 restart
sudo /opt/bitnami/ctlscript.sh restart apache
https://stackoverflow.com/questions/44038456/how-to-setup-apache-server-for-react-route
https://raddy.dev/blog/deploy-your-mern-stack-app-on-aws-lightsail-in-minutes/#h-create-virtual-hosts-for-client-server
https://docs.bitnami.com/aws/apps/wordpress/administration/force-https-apache/

## local build bash

```
export REACT_APP_API_URI=http://13.210.182.8:3001/api/ && yarn build:combinecsr --force
export REACT_APP_API_URI=http://127.0.0.1:3001/api/ && yarn build:combinecsr --force
```

place build in `opt/bitnami/apache/htdocs`

```
yarn install
yarn start:api
```

- screen management

  ```
  screen
  screen -r
  screen -ls
  exit
  screen -S session_name
  screen -r 10835.api
  screen -X -S [session # you want to kill] quit
  ```

  ```
  sudo /opt/bitnami/ctlscript.sh status
  sudo /opt/bitnami/ctlscript.sh restart mongodb
  sudo /opt/bitnami/ctlscript.sh stop mongodb
  sudo /opt/bitnami/ctlscript.sh start mongodb
  mongosh
  ```

- nginx

```
sudo chmod -R 777 usr/share/nginx/html
```

- apache

```
sudo /opt/bitnami/ctlscript.sh restart apache
```

- yarn build --filter=boc_queue_schema

## api env mongoose

```
MONGODB_URI= "mongodb://0.0.0.0:27017" # Must not be localhost
MONGODB_DATABASE= "boc_queue_mongodb_local"
MONGODB_USER= "admin"
MONGODB_PASS= "admin"
PORT= "3001"
```

"ts-node" "Unknown file extension" .ts
https://stackoverflow.com/questions/62096269/cant-run-my-node-js-typescript-project-typeerror-err-unknown-file-extension
https://github.com/TypeStrong/ts-node/issues/2100
node --loader ts-node/esm ./server.ts

## change lightsail timezone

```
date
sudo cp /etc/localtime /etc/localtime.bak
sudo ln -sf /usr/share/zoneinfo/Australia/Sydney /etc/localtime
```

https://www.geeksforgeeks.org/set-the-time-zone-in-amazon-ec2/

## known bugs

https://github.com/TypeStrong/ts-node/issues/2026
https://github.com/TypeStrong/ts-node/issues/2085
