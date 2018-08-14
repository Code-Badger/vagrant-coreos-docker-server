# Vagrant CoreOS Docker Server

A Vagrant provision for Docker to run multiple app containers on CoreOS Server.

## Installed Applications
* Redmine: Project Management Web App
* ResourceSpace: Digital Asset Management
* Gitbucket: Git Server
* Etherpad: Real-time Wordpad
* EtherCalc: Real-time Spreadsheets
* manet: Web Screenshot Server
* MySQL: Relational Database
* Redis: NoSQL

### System Requirements

* Vagrant 1.8.1 or later with NFS support

## How to use

```
git clone url
cd vagrant-coreos-docker-server
vagrant up
```

To SSH login and manually config containers.

```
cd vagrant-coreos-docker-demo
vagrant ssh
cd dockerfiles

docker-compose stop
docker-compose up -d
docker-compose logs
```

## Default Passwords

* ResourceSpace: admin/admin
* Redmine: admin/admin
* Gitbucket: root/root
* MySQL(root): please\_enter\_your\_password

#### Network

This demo is configured as internal network. You can access the apps with localhost's port 8888(Web), 33060(MySQL) and 29418(gitbucket's SSH).

#### Data Storage

All data will be saved in "data.vdi". This virtual image must be preserved when destroying the Vagrant.

#### CAUTION
DO NOT EXECUTE `vagrant destroy` WITHOUT DETACHING "data.vdi"!  
Vagrant will delete all external storage file when you destroy the VM, so you have to detach the storage with VirtualBox GUI.

### CoreOS

"cloud-config" is almost default but added mount settings to use the external disks.

===

### Docker

This demo uses docker-compose to manage docker containers.

#### Nginx

nginx is configured as a reverse proxy. It also run as a docker container.
