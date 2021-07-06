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
sudo -s
vim /etc/nginx/nginx.conf
server {
    ... Add the following config
    
    location / {
        proxy_set_header Host              $http_host;
        proxy_set_header X-Real-IP         $remote_addr;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_set_header X-Forwarded-For   $proxy_add_x_forwarded_for;
        proxy_pass http://127.0.0.1:3000/;
    }
    
    ...
}

⇨ ESC > :x! > ENTER to save and exit
```

```bash
sudo systemctl reload nginx (or sudo systemctl restart nginx)
sudo systemctl status nginx
```

## Other CMD

```
netstat -anp | grep 3000
```
