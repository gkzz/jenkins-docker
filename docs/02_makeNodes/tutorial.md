## 02. Make New Nodes as Slave

- Click "Manage Jenkins" on ${PUBLIC_IP}:8080 > "Manage Nodes" > "New Node"
- Write Your Node name like slave01
- Check `Parmament Agent`
- Press "OK"

<img src="/docs/02_makeNodes/img/setNewNode1.png" alt="Select installation plan" style="max-width:5%;">

- Write the following items
  - Name
  - Remote root directory
    - cf. root@slave01:/home/jenkins# pwd
          /home/jenkins
  
- Set each value on the following items

  | Item                           | Value                               |
  |--------------------------------|-------------------------------------|
  | Usage                          | Use this node as much as possible   |
  | Launch method                  | Launch agent agents via SSH         |
  | Host Key Verification Strategy | Non verifying Verification Strategy |


  - Lanch method > Host

- Press Credentials > "Add", and select "jenkins"

<img src="/docs/02_makeNodes/img/setNewNode2.png" alt="Select installation plan" style="max-width:5%;"> 

- Select `SSH Username with private key` of "kind"
- Write the following items
  - ID
  - Username
- Check the button between Private Key and Enter directly, and press "Add"
- Copy and paste `$YOUR_PRIVATE_KEY on master cluster`
- Press "Add"
- Press "none", and select "jenkins"
- Press "Save", after pop-up window closes

<img src="/docs/02_makeNodes/img/setNewNode3.png" alt="Select installation plan" style="max-width:5%;">

- Just a minute!
  - Press "Refresh status" or execute reload, if you would like not to wait until the update is finished 

<img src="/docs/02_makeNodes/img/notUpdated.png" alt="Select installation plan" style="max-width:5%;">

- The update is finished

<img src="/docs/02_makeNodes/img/updated.png" alt="Select installation plan" style="max-width:5%;">