# WordPress Free Forever

```bash
# sudo apt update
# apt list --upgradeable
# sudo apt upgrade

# video:2
# sudo fallocate -l 4G /swapfile
sudo fallocate -l 8G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo nano /etc/fstab

/swapfile none swap sw 0 0

curl https://get.docker.com > install-docker.sh
chmod 100 install-docker.sh
sudo ./install-docker.sh
sudo usermod -aG docker dev_turtlewolfe
sudo docker container ls
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
git clone https://github.com/TurtleWolf/wordpressMathews
cp -r wordpressMathews carGambler
# cd carGambler
cp -r wordpressMathews crudGames
# cd crudGames
cp -r wordpressMathews geoLARP
# cd geoLARP
cp -r wordpressMathews PohlnerLandscaping
# cd pohlnerlandscaping
cp -r wordpressMathews TurtleWolfe
# cd TurtleWolfe
cp -r wordpressMathews ScriptHammer
sudo rm -rf wordpressMathews
cd ScriptHammer
# cd wordpressMathews/
nano .env
chmod 400 .env
sudo docker-compose up -d

# video:4
# http:// general settings, lower case.com

nano docker-compose.yml
nano docker-compose.yml
# 8080:80
# chmod 400 docker-compose.yml
sudo docker-compose down
docker-compose up -d
sudo docker-compose up -d
docker ps
sudo docker ps

# 6:3-50 inaccessible
sudo apt install -y nginx
sudo nano /etc/nginx/sites-available/www.scripthammer.com.conf
# 7:30 private window to dodge cache
server {
    root /var/www/html;
    listen 80;
    listen [::]:80;
    server_name scripthammer.com www.scripthammer.com;
    location / {
        proxy_pass http://127.0.0.1:8080;
        proxy_redirect off;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Host $server_name;
        proxy_set_header X-Forwarded-Proto $scheme;
        }
    }
# 7:30 private window to dodge cache

sudo cp /etc/nginx/sites-available/www.scripthammer.com.conf /etc/nginx/sites-available/www.carGambler.com.conf
sudo cp /etc/nginx/sites-available/www.scripthammer.com.conf /etc/nginx/sites-available/www.crudGames.com.conf
sudo cp /etc/nginx/sites-available/www.scripthammer.com.conf /etc/nginx/sites-available/www.geoLARP.com.conf
sudo cp /etc/nginx/sites-available/www.scripthammer.com.conf /etc/nginx/sites-available/www.PohlnerLandscaping.com.conf
# sudo cp /etc/nginx/sites-available/www.scripthammer.com.conf /etc/nginx/sites-available/www.scripthammer.com.conf
sudo cp /etc/nginx/sites-available/www.scripthammer.com.conf /etc/nginx/sites-available/www.TurtleWolfe.com.conf

sudo nano /etc/nginx/sites-available/www.carGambler.com.conf
sudo nano /etc/nginx/sites-available/www.crudGames.com.conf
sudo nano /etc/nginx/sites-available/www.geoLARP.com.conf
sudo nano /etc/nginx/sites-available/www.PohlnerLandscaping.com.conf
# sudo nano /etc/nginx/sites-available/www.scripthammer.com.conf
sudo nano /etc/nginx/sites-available/www.TurtleWolfe.com.conf

    # 8081   3301   server_name cargambler.com www.cargambler.com;
    # 8082   3302   server_name crudgames.com www.crudgames.com;
    # 8083   3303   server_name geolarp.com www.geolarp.com;
    # 8084   3304   server_name pohlnerlandscaping.com www.pohlnerlandscaping.com;
    # 8080   3306   server_name scripthammer.com www.scripthammer.com;
    # 8088   3308   server_name turtlewolfe.com www.turtlewolfe.com;

sudo ln -s /etc/nginx/sites-available/www.carGambler.com.conf /etc/nginx/sites-enabled/www.carGambler.com.conf
sudo ln -s /etc/nginx/sites-available/www.crudGames.com.conf /etc/nginx/sites-enabled/www.crudGames.com.conf
sudo ln -s /etc/nginx/sites-available/www.geoLARP.com.conf /etc/nginx/sites-enabled/www.geoLARP.com.conf
sudo ln -s /etc/nginx/sites-available/www.PohlnerLandscaping.com.conf /etc/nginx/sites-enabled/www.PohlnerLandscaping.com.conf
sudo ln -s /etc/nginx/sites-available/www.scripthammer.com.conf /etc/nginx/sites-enabled/www.scripthammer.com.conf
sudo ln -s /etc/nginx/sites-available/www.TurtleWolfe.com.conf /etc/nginx/sites-enabled/www.TurtleWolfe.com.conf

sudo service nginx restart

# video:5
sudo apt install software-properties-common && sudo apt update
# sudo apt autoremove
sudo add-apt-repository ppa:certbot/certbot
sudo apt update
sudo apt install -y python-certbot-nginx
# sudo apt install -y python3-certbot-nginx
sudo certbot --nginx -d ScriptHammer.com -d www.ScriptHammer.com
# cat www.ScriptHammer.com.conf
sudo certbot --nginx -d carGambler.com -d www.carGambler.com
sudo certbot --nginx -d crudGames.com -d www.crudGames.com
sudo certbot --nginx -d geoLARP.com -d www.geoLARP.com
sudo certbot --nginx -d PohlnerLandscaping.com -d www.PohlnerLandscaping.com
sudo certbot --nginx -d TurtleWolfe.com -d www.TurtleWolfe.com
sudo service nginx restart
sudo systemctl status nginx
cd ScriptHammer
# docker-compose up -d
# sudo docker-compose up -d
cd wp-app
sudo nano wp-config.php

if ($_SERVER['HTTP_X_FORWARDED_PROTO'] == 'https')
    $_SERVER['HTTPS']='on';

if (isset($_SERVER['HTTP_X_FORWARDED_HOST'])) {
    $_SERVER['HTTP_HOST'] = $_SERVER['HTTP_X_FORWARDED_HOST'];
}
sudo service nginx restart
# http  (!!S!!) :// general settings, lower case.com
docker-compose stop
docker-compose start
/etc/letencrypt
sudo crontab -e
45 2 * * * certbot renew > /tmp/certbotrenew.log
```
