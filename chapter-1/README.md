# Provision the Ubuntu Server (using 18.04)

- host01
- host02

## Chapter 1

* first we reinstall docker-engine (from docker.io to docker-ce)

```
#!/bin bash
apt-get remove docker docker-engine docker.io containerd runc
apt-get update
apt-get -y install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
apt-get update
apt-get -y install docker-ce docker-ce-cli containerd.io
```

## Install Rancher Server on host01

```
docker run --privileged -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher
```

## Configure Rancher

Go to https://host1:8080