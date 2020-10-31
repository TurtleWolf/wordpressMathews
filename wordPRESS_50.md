# WordPress Free ForEver

## **#2 SwapFile**

```bash
sudo apt update
apt list --upgradeable
sudo apt upgrade
sudo apt update
top
sudo fallocate -l 4G /swapfile
cd /
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
top
sudo apt install -y nano
sudo nano /etc/fstab
```

### **7:18**

```bash 7:18
/swapfile none swap sw 0 0
```

```bash
sudo reboot
top
curl https://get.docker.com > install-docker.sh
# chmod 755 install-docker.sh
chmod 100 install-docker.sh
sudo ./install-docker.sh
sudo usermod -aG docker dev_turtlewolfe
sudo docker container ls
sudo reboot
docker container ls
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
sudo apt install -y git
```

make sure you're back in home ~

```
git clone https://github.com/chrisbmatthews/wordpress-docker-compose.git
cd wordpress-docker-compose/
```

### **11:45 also edit passwords at this point**

```bash
nano .env
    IP=127.0.0.1
    DB_ROOT_PASSWORD=alphaa
    DB_NAME=charlie
chmod 600 .env
sudo nano docker-compose.yml

    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_NAME: "${DB_NAME}"
      WORDPRESS_DB_USER: root
      WORDPRESS_DB_PASSWORD: "${DB_ROOT_PASSWORD}"

chmod 600 docker-compose.yml
docker-compose up -d
docker container ls
```

## **#3 Point DNS @ Cloud IP**

1. static IP
1. DNS @ A & www CNames 3:13

```bash
dig scripthammer.com
```

## #4 NGINX Reverse Proxy

### **:50** setting, general 2 URLs

### **3:55**

```bash
docker container ls
nano docker-compose.yml
docker-compose down
docker ps
docker ps -a
docker-compose up -d
docker ps
```

### **7:15** defaults to port 80

```bash
sudo apt install -y nginx
cd /etc/nginx
cd sites-available/
nano default
sudo nano www.ScriptHammer.com.conf
```

```conf
server {
root /var/www/html;
listen 80;
listen [::]:80;
server_name scripthammer.com www.scripthammer.com;
location / {
      proxy_pass http://127.0.0.1:8080;
      proxy_redirect off;
      proxy_set_header Host $host;
      proxy_set_header   X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header   X-Forwarded-Host $server_name;
      proxy_set_header X-Forwarded-Proto \$scheme;
  }
}
```

### (#5 10:54)

```bash
cd ..
cd sites-enabled/
sudo ln -s /etc/nginx/sites-available/www.ScriptHammer.com.conf www.ScriptHammer.com.conf
cat www.ScriptHammer.com.conf
sudo service nginx restart

sudo apt autoremove
```

## **#5 HTTPS Let's Encrypt**

### **3:00**

```bash
sudo apt install software-properties-common && sudo apt update
```

<!-- sudo apt update   -->
<!-- apt list --upgradeable   -->
<!-- sudo apt upgrade   -->

```bash
sudo add-apt-repository ppa:certbot/certbot
sudo apt update
sudo apt install -y python-certbot-nginx
```

<!-- choose location   -->

```bash
cd ..
cd sites-available/
sudo certbot --nginx -d scripthammer.com -d www.scripthammer.com
```

<!-- sudo certbot --nginx -d scripthammer.com -->
<!-- redirect unsecure   -->

```bash
cat www.ScriptHammer.com.conf
sudo service nginx restart
```

### **8:40**

```bash
cd wordpress-docker-compose/
cd wp-app/
sudo vi wp-config.php
```

```php
if ($_SERVER['HTTP_X_FORWARDED_PROTO'] == 'https')
    $\_SERVER['HTTPS']='on';

if (isset($_SERVER['HTTP_X_FORWARDED_HOST'])) {
    $\_SERVER['HTTP_HOST'] = \$\_SERVER['HTTP_X_FORWARDED_HOST'];
}
```

```php
define('FS_METHOD','direct');
```

```bash
cd ..
docker-compose stop
docker-compose start
```

### **11:21** wp-admin/options-general.php

1. https
1. https

### **11:40**

```bash
docker-compose stop && docker-compose start
sudo certbot renew
cd /etc
cd /letsencrypt
cd letsencrypt/
sudo crontab -e
```

### **13:12**

```bash
45 2 * * * certbot renew > /tmp/certbotrenew.log
```
