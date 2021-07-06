# VTI Seminar: Project Knowledge Management
Install Docker and Git on Amazon Linux 2

## Install Docker

```bash
sudo yum install -y docker
docker -v

sudo systemctl start docker
sudo systemctl enable docker

sudo usermod -a -G docker ec2-user
sudo docker info
```

## Install Docker-Compose

```bash
sudo curl -L https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose -v
```

## Install Git

```bash
sudo yum install -y git
git --version
```

## Install Nginx

```bash
sudo amazon-linux-extras install -y nginx1
nginx -v

sudo systemctl start nginx
sudo systemctl enable nginx
```

```bash
cat > /etc/nginx/conf.d/growi.conf
server {
    listen      80;
    server_name growi.com;

    proxy_set_header Host              $http_host;
    proxy_set_header X-Real-IP         $remote_addr;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Forwarded-For   $proxy_add_x_forwarded_for;

    location / {
        proxy_redirect off;
        proxy_pass http://127.0.0.1:3000/;
    }
}

⇨ CTRL-D to save and exit
```

```bash
sudo systemctl reload nginx (or sudo systemctl restart nginx)
sudo systemctl status nginx
```

## Other CMD

```
netstat -anp | grep 3000
```
