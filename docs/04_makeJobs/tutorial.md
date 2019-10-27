## Make New jobs

- Press "New Item" on ${PUBLIC_IP}:8080
- Enter your new item's name
- Select `Pipeline` and "OK"

<img src="/docs/makeJobs/img/selectPipeline.png" alt="Select Pipeline" style="max-width:5%;">

- Scroll down to `Pipeline`
- Press "Pipeline Syntax"
- Press "archiveArtifacts: Archive the artifacts", and change it to `sh: Shell Script`
- Enter commands that you execute on the window next to `Shell Script` as bellow;

```
ls
pwd
ping -w 3 -c 1 www.google.com
```

<img src="/docs/makeJobs/img/enterShellScript.png" alt="Enter shellscript" style="max-width:5%;">

- Press `Generate Pipeline Script`
- Copy the script

```
sh label: '', script: '''ls
pwd
ping -w 3 -c 1 www.google.com'''

```
- Come back to `setting screen, ${PUBLIC_IP}:8080/job/${JOB_NAME}/configure`
- Copy the following and paste it on the window next to the "Script"

```
node("${SLAVENAME}") {
    ${SHELLSCRIPT}
}

```
- Modify ${SLAVENAME} and ${SHELLSCRIPT}
- My pipeline script is as bellow;

```
node("slave01") {
    sh label: '', script: '''ls
    pwd
    ping -w 3 -c 1 www.google.com'''
}

```

- Press "Apply" and "Save"

<img src="/docs/makeJobs/img/PastePipelinescript.png" alt="Paste pipeline script" style="max-width:5%;">


