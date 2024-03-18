# Lightsail Deployment

Download and move generated ssh key upon instance creation to `C:\Users\yourusername\.ssh`.
Default password can be found in `home/bitnami/bitnami_application_password`

- SSH Connect

```
ssh -i boc-queue-dev-lightsail.pem bitnami@13.210.182.8
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
ssh -i boc-queue-dev-lightsail.pem -N -f -L 3801:localhost:27017 bitnami@13.210.182.8
```

- PM2

```
sudo yarn global add pm2
pm2 start "yarn start" --name boc_queue
pm2 stop
pm2 ls
pm2 monit
```

- Install Docker Compose

```
sudo apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg2 \
    software-properties-common

curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
```

- nginx

```
uname -a
sudo apt update
sudo apt install nginx
```

- lightsail
  networking firewall
  Custom TCP 3001

- serve

```
yarn global add serve
yarn serve -p 3002 -s build
yarn serve -p 3003 -s build.admin
```

- apache

  ```
  <VirtualHost *:8080>
  ServerName example.com
  DocumentRoot /var/www/httpd/example.com

    <Directory "/var/www/httpd/example.com">
      ...

      RewriteEngine On
      # Don't rewrite files or directories
      RewriteCond %{REQUEST_FILENAME} -f [OR]
      RewriteCond %{REQUEST_FILENAME} -d
      RewriteRule ^ - [L]
      # Rewrite everything else to index.html to allow html5 state links
      RewriteRule ^ index.html [L]
    </Directory>
  </VirtualHost>
  ```

  sudo service apache2 restart
  sudo /opt/bitnami/ctlscript.sh restart apache
  https://stackoverflow.com/questions/44038456/how-to-setup-apache-server-for-react-route

- local build bash

  ```
  export REACT_APP_API_URI=http://13.210.182.8:3001/api/ && yarn build:combinecsr --force
  ```

  place build in `opt/bitnami/apache/htdocs`

  ```
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
  sudo /opt/bitnami/ctlscript.sh restart mongodb
  ```

