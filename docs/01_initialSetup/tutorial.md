## 01. Initial Setup


### Installtion

- Open your Jenkins management console on ${PUBLIC_IP}:8080

- Set your initialAdminPassword, and press "Continue"

<img src="/docs/01_initialSetup/img/setInitPw.png" alt="Set your initialAdminPassword" style="max-width:5%;">

- Select installation plan
  - I chose `Install suggested plugins`

  <img src="/docs/01_initialSetup/img/installPlugin.png" alt="Select installation plan" style="max-width:5%;">


- Create user
 - You have to write `E-mail address in the correct format` as bellow;

 sample@sample.com

<img src="/docs/01_initialSetup/img/createUser.png" alt="Create user" style="max-width:5%;">

- Press "Save and Continue"

<img src="/docs/01_initialSetup/img/createUser2.png" alt="Create user" style="max-width:5%;">

- Press "Save and Finish"

<img src="/docs/01_initialSetup/img/beginInstallation.png" alt="Begin installation" style="max-width:5%;">


### Generate Private key on Master Cluster
```
root@master:/# mkdir -p /var/jenkins_home/.ssh && ssh-keygen -t rsa -b 4096 -C "sample@sample.com" 
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa): /var/jenkins_home/.ssh/$YOUR_PRIVATE_KEY
Enter passphrase (empty for no passphrase):  [Press Enter]
Enter same passphrase again: [Press Enter]

...
root@master:/# exit
ubuntu@hostname ~/jenkins-docker (master) $ 
```


### Set Your Pub Key to conf/secrets.env
```
ubuntu@hostname ~/jenkins-docker (master) $ echo "JENKINS_SLAVE_SSH_PUBKEY=" > conf/secrets.env && \
cat jenkins_home/.ssh/id_rsa_jenkins_master.pub >> conf/secrets.env
ubuntu@hostname ~/jenkins-docker (master) $ cat conf/secrets.env      //Modify like conf/secrets.env.tmpl
JENKINS_SLAVE_SSH_PUBKEY=ssh-rsa xxxxxxxxxxxxxxxxxxxx== sample@sample.com
```
- jenkins_home direcotyr on host are mounted into var/jenkins_home directory on master cluster
- So, $YOUR_PUB_KEY also exists on hosts, as the key are generated on master cluster. 


### Checkout if authorized_keys on slave cluster exists or not
```
ubuntu@hostname ~/jenkins-docker (master) $ docker-compose up -d
ubuntu@hostname ~/jenkins-docker (master) $ docker-compose exec slave01 bash
root@slave01:/home/jenkins# pwd
/home/jenkins
root@slave01:/home/jenkins# cat /home/jenkins/.ssh/authorized_keys
ssh-rsa xxxxxxxxxxxxxxxxxxxx== sample@sample.com
```

Congratulations!!