## FAQ

- Cannot acccess Jenkins runnning on ec2-instance

  - Checkout your security group for the ec2-instance.

  - Here are the following neccessary rules:

    | Type            | Port Range | Source        | Desc                    |
    |-----------------|------------|---------------|-------------------------|
    | SSH             | 22         | My Wifi       | SSHFromLocal            |
    | HTTP            | 80         | 0.0.0.0/0     | FullOpen80              |
    | HTTP            | 80         | ::/0          | FullOpen80              |
    | Custom TCP Rule | 8080       | My Wifi       | onlyJenkinsGUIFromLocal |
    | All TCP         | 0-65535    | x.x.x.x/22    | FromGithubWebhook       |

  - As shown below, the IP address of GitHub is described at [meta](https://api.github.com/meta)
  - The IP address of hooks is allowed by the security group

  <img src="/docs/x_faq/img/securityGroup.png" alt="security group" style="max-width:5%;">

- Jenkins Setup Wizard Blank
  Just move on ${PUBLIC_IP}:8080/restart or localhost:8080/restart

  <img src="/docs/x_faq/img/setupWizardBlank.png" alt="Setup Wizard Blank" style="max-width:5%;">
  
