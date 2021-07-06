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
git -version
```
