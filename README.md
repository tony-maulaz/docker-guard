## Start
-  run docker-compose `docker-compose up`
-  if error permission php init
  - `sudo chmod -R 777 config/` (pas la bonne solution mais pour du test)
-  if error with mysql, restart docker-compose

### MYSQL
- In a bash `docker exec -it mysql_guard bash`
- In the mysql container
  -  `mysql -u root -p` (see .env for password)
  -  Show user : `select Host,User from mysql.user;`
  -  If not exist : `CREATE USER 'laravel'@'%' IDENTIFIED WITH mysql_native_password BY 'Root1234';`
  -  `GRANT ALL PRIVILEGES ON *.* TO 'laravel'@'%';`
  -  `FLUSH PRIVILEGES;`

### Apache
-  `docker exec -it web bash`
-  `cd /etc/apache2/sites-available`
-  `a2enmod rewrite.load`
-  `a2ensite guard.conf`
-  `service apache2 reload`

### Php
-  `docker exec -it php bash`
-  `cd /var/www/html`
-  Change user in `php/config/.gitconfig`
  - git config --global user.name "Your Name"
  - git config --global user.email "youremail@yourdomain.com"
-  clone code `git clone https://github.com/... .`
-  if permission not good for `storage` : ` chmod -R a+w storage/`
-  `composer install`
-  `npm install`

### Develop
-  `npm run watch`: watch if js files change

### Laravel
-  `php artisan make:controller ImageController`

### Open code
-  Inside VS Code `Attach to running container -> php`

### Access
  - `127.0.0.1:8080`

### Docker
-  `docker-compose up -d`
-  `docker exec -it php bash`
-  `docker container ls`
-  `docker container prune`
-  `docker system prune`

### Alias bash
-  `alias dcls='docker container ls --format "table {{.ID}}\t{{.Image}}\t{{.Names}}"'`
-  `alias dexec='docker exec -it'`

### Update node
- `npm cache clean -f`
- `npm install -g n`
- `n latest`
