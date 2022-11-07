## Prod Server Installation

### Docker Installation

Get and install docker via script for linux:

```
 curl -fsSL https://get.docker.com -o get-docker.sh
 sudo sh get-docker.sh
```
### Docker Compose Installation
```
sudo apt-get remove docker-compose
sudo rm /usr/local/bin/docker-compose
pip uninstall docker-compose
```
```
# curl + grep
VERSION=$(curl --silent https://api.github.com/repos/docker/compose/releases/latest | grep -Po '"tag_name": "\K.*\d')

# curl + jq
VERSION=$(curl --silent https://api.github.com/repos/docker/compose/releases/latest | jq .name -r)
```
```
DESTINATION=/usr/local/bin/docker-compose
sudo curl -L https://github.com/docker/compose/releases/download/${VERSION}/docker-compose-$(uname -s)-$(uname -m) -o $DESTINATION
sudo chmod 755 $DESTINATION
```

### Docker Compose Installation

For stable version download with `curl`, run the following command

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.28.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

If it fails then do the following

```
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

Check

```
docker-compose --version
```

If you want to install in python environment

```
sudo pip install docker-compose
```

To run docker-compose

```
docker-compose -f local.yml up --build -d
```
Facing issue with docker compose version then go through this [link](https://stackoverflow.com/a/49839172/7195890)

### Miniconda Installation

Go to this [url](https://docs.conda.io/en/latest/miniconda.html#linux-installers) and download the installer script for linux and run the following command:

```
bash Miniconda3-latest-Linux-x86_64.sh
```

# RHEL Docker Setup

```
# sudo yum remove docker docker-common docker-selinux docker-engine-selinux docker-engine docker-ce
# sudo yum install -y yum-utils device-mapper-persistent-data lvm2
# sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
# sudo yum install docker-ce
```

If the error persits

```
# yum-config-manager --enable REPOSITORY
# yum install docker
```

If the error comes again

```
# subscription-manager register
# subscription-manager list --available
# subscription-manager attach --pool=pool_id
# subscription-manager repos --enable=rhel-7-server-rpms
# subscription-manager repos –enable=rhel-7-server-extras-rpms
# sudo yum remove docker docker-common docker-selinux docker-engine-selinux docker-engine docker-ce
# sudo yum install -y yum-utils device-mapper-persistent-data lvm2
# sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
# sudo yum install docker-ce
# yum-config-manager --enable REPOSITORY
# yum install docker
# systemctl start docker.servic
```
## Installing WGET

```
sudo dnf install wget
```

## To install Nano

```
sudo yum install nano
```

## To open port on Cent OS 8

```
firewall-cmd --zone=public --add-port=55555/tcp --permanent
```

## Miniconda Installation on RHEL8

- [Resource](https://deeplearning.lipingyang.org/2018/12/24/install-miniconda-on-centos-7-redhat-7/)
