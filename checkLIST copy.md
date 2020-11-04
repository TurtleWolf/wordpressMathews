# WordPress Free Forever

```bash
# sudo apt update
# apt list --upgradeable
# sudo apt upgrade


# sudo docker container ls
# git clone https://github.com/TurtleWolf/wordpressMathews
cd wordpressMathews/
chmod 400 docker-compose.yml
sudo docker-compose up -d
# sudo docker-compose down



docker-compose down
# sudo docker-compose down
nano docker-compose.yml
sudo nano docker-compose.yml
docker-compose up -d
sudo docker-compose up -d
docker ps
sudo docker ps
# sudo apt install -y nginx
sudo nano /etc/nginx/sites-available/www.pohlnerlandscaping.com.conf

server {
    root /var/www/html;
    listen 80;
    listen [::]:80;
    server_name pohlnerlandscaping.com www.pohlnerlandscaping.com;
    location / {
        proxy_pass http://127.0.0.1:8080;
        proxy_redirect off;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Host $server_name;
        proxy_set_header X-Forwarded-Proto \$scheme;
        }
    }

sudo ln -s /etc/nginx/sites-available/www.pohlnerlandscaping.com.conf /etc/nginx/sites-enabled/www.pohlnerlandscaping.com.conf
sudo service nginx restart

sudo apt install software-properties-common && sudo apt update
sudo add-apt-repository ppa:certbot/certbot
sudo apt update
sudo apt install -y python-certbot-nginx
sudo apt install -y python3-certbot-nginx
sudo certbot --nginx -d pohlnerlandscaping.com -d www.pohlnerlandscaping.com
sudo service nginx restart

cat www.pohlnerlandscaping.com.conf
cd wordpressMathews
docker-compose up -d
sudo docker-compose up -d
cd wp-app
sudo nano wp-config.php

if ($_SERVER['HTTP_X_FORWARDED_PROTO'] == 'https')
    $_SERVER['HTTPS']='on';

if (isset($_SERVER['HTTP_X_FORWARDED_HOST'])) {
    $_SERVER['HTTP_HOST'] = $_SERVER['HTTP_X_FORWARDED_HOST'];
}
```
