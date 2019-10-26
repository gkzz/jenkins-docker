## 03. Install Slack Notification Plugin

- Go to ${YOUR_SLACK_APP_DIRECTORY}
  - cf. https://${YOUR_WORKSPACE}.slack.com/apps
- Enter `jenkins` on search window
- Press "Jenkins CI", and "Add to Slack"
- Select channels to post
- Press "Add Jenkins CI integration"
- Copy `Token`
- Press "Save Settings"

<img src="/docs/03_installSlackPlugin/img/slackApp.png" alt="Config slack app" style="max-width:5%;">

- Click "Manage Jenkins" on ${PUBLIC_IP}:8080 > "Manage Plugins" > "Available"
- Search by `slack`
- Click `Slack Notification`, and "Install without restart"

<img src="/docs/03_installSlackPlugin/img/installSlackNotificationPlugin.png" alt="install Slack Notification Plugin" style="max-width:5%;">

- Check "Restart"

<img src="/docs/03_installSlackPlugin/img/restartJenkins.png" alt="Get restart" style="max-width:5%;">

- Execute reload, when the page is displayed as bellow;

<img src="/docs/03_installSlackPlugin/img/executeReload.png" alt="Get restart" style="max-width:5%;">

- Click "Manage Jenkins" on ${PUBLIC_IP}:8080 > "Configure System", and scroll down to `slack configuration`
- Write the following items
  - Slack > Workspace
    - cf. https://${YOUR_WORKSPACE}.slack.com
  - Slack > Default channel / member id
    - e.g. general
- Press "Add", and select "jenkins"

<img src="/docs/03_installSlackPlugin/img/configSlackPlugin1.png" alt="Config slack plugin" style="max-width:5%;">

- Press "Username with password", and change it to `Secret text`
- Paste "Token" you copied for "Secret"
- Press "Add" (, the pop-up window will close automaticaly)

<img src="/docs/03_installSlackPlugin/img/configSlackPlugin2.png" alt="Config slack plugin" style="max-width:5%;">

- Press "none", and change it to `jenkins`
- Press "Apply", and "Save"

 	