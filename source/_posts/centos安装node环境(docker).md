---
title: centos安装node和docker
date: 2023-02-23 11:15:00
tags: 后端
---

### Node
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
nvm install node
yum update
yum install -y git
```

### Docker

```
 sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
2. sudo yum install -y yum-utils
3. sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
    
4. sudo yum install docker-ce docker-ce-cli containerd.io
5. sudo systemctl start docker
6.sudo curl -L "https://github.com/docker/compose/releases/download/1.27.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
7. sudo chmod +x /usr/local/bin/docker-compose
8. sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

## 报错就：
yum install -y https://download.docker.com/linux/centos/7/x86_64/stable/Packages/containerd.io-1.2.6-3.3.el7.x86_64.rpm

```