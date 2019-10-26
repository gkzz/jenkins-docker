# Jenkins on Docker Containers (Master/Slave)

## TL;DR

- Build a Jenkins container as master cluster
```
ubuntu@hostname ~/jenkins-docker (master) $ git clone git@github.com:gkzz/jenkins-docker.git
ubuntu@hostname ~/jenkins-docker (master) $ docker-compose -f docker-compose-init.yml up -d
ubuntu@hostname ~/jenkins-docker (master) $ docker-compose exec master bash
root@master:/# cat /var/jenkins_home/secrets/initialAdminPassword
xxxxxxxxxxxxxxxxxxxxxxxx
```


## Table of Contents

- Technologies Used
- Usage
  - Initial Setup
  - Make New Nodes as Slave
  - Make New jobs


- FAQ


## Technologies Used
- Docker 19.03.4
  - Jenkins Image (Master) jenkins/jenkins:lts
    - Jenkins ver. 2.190.1 (From Web Potal)
  - Jenkins Image (Slave01) jenkins/ssh-slave
- docker-compose 1.24.1
- AWS (EC2, VPC, EIP, etc)
  - Ubuntu 18.04.3 LTS


## Usage

- [01 Initial Setup](/docs/01_initialSetup/tutorial.md)

- [02 Make New Nodes as Slave](/docs/02_makeNodes/tutorial.md)

- [03. Install Slack Notification Plugin](/docs/03_installSlackPlugin/tutorial.md)

- [04 Make New jobs](/docs/04_makeJobs/tutorial.md)


## Notes

```
gkz@localhost ~/jenkins-docker (master) $ tree -L 2 -I jenkins_home
.
├── conf
│   ├── secrets.env
│   └── secrets.env.tmpl
├── docker-compose-init.yml
├── docker-compose.yml
├── docs
│   ├── 01_initialSetup
│   ├── 02_makeNodes
│   ├── 03_installSlackPlugin
│   ├── 04_makeJobs
│   └── x_faq
├── LICENSE
└── README.md

8 directories, 6 files

```

## FAQ

[This page may help you to solve your problems](docs/x_faq/tutorial.md)

e.g. Cannot acccess Jenkins runnning on ec2-instance

