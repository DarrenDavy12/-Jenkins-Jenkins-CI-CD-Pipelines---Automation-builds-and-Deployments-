# (Jenkins) Jenkins CI/CD Pipelines - Automation builds and Deployments

[Summary]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Summary%2000c782bf9d614abbb1f2c77531780718.md)

## Setup:

First inside the terminal, I ran this command to get Jenkins up and running in Docker.

We are going to expose two ports 8080:8080 but we going to connect to 50000 which is used internally by Jenkins. While creating a volume on a local machine and Docker take care of this for us. It’s a folder to store all the information for Jenkins. It is useful if for whatever reason, a docker container stops. We can re-run it using this command and we’ll have all our information saved. 

cmd: `docker run -p 8080:8080 -p 50000:50000 --restart=on-failure -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11`

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled.png)

Copy the given password and enter it in terminal for further installation. (Store it somewhere safe on local machine) 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%201.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%202.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%203.png)

Once the installation is complete, I went to my browser, in a new tab and in the url typed [localhost:8080](http://localhost:8080) and I get this page, which means we have connect to the Jenkins port 8080. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%204.png)

Then I entered the password I copied from the Jenkins command I ran earlier and hit continue. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%205.png)

I select the install suggested plugins.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%206.png)

I waited until all the plugins are installed. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%207.png)

I clicked skip and continue as admin at the bottom. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%208.png)

Then I clicked Save and Finish. On the next page I clicked start using Jenkins.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%209.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2010.png)

Now I have Jenkins installed.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2011.png)

## Create New Jobs:

I go to create a job.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2012.png)

- Freestyle project - most common, it’s like a blank slate, create whatever we want
- Pipeline - Create declarative pipelines, Continuous Integration and Continuous Deployment
- Multi-configuration project - Not used as often, run same jobs but with slightly different parameters
- Folder - Organize our jobs, folder for testing, folder for build
- MultiBranch Pipeline - Most powerful pipeline, jobs been setup can hold every single branch of that repo, we don’t have to set another job when part of a team, mulit-branch pipeline will take care about for you
- Organization Folder - Similar to multibranch but it scans for repos from Source control Managers - Github etc

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2013.png)

Moving on, I gave a name for the project and selected freestyle project and clicked ok. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2014.png)

Next I scroll down to the bottom and click the Add build step and selected Execute shell.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2015.png)

Then I added this command (in image below) inside the shell which has popped up and afterwards I hit Save.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2016.png)

Once we are shown back to the dashboard and click build now. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2017.png)

At the bottom, I click on #1 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2018.png)

I go to console output and see the command message I wrote earlier and my little Jenkins job is up and running. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2019.png)

## Pipelines:

First I got into VScode and click open folder and make a new folder called `Jenkins` and open it up in VScode. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2020.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2021.png)

I create a new file inside the folder called `Jenkinsfile` 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2022.png)

I create my pipeline here, and then copy and paste it inside the Jenkins job. 

If I logged out of Jenkins the credentials I must use are:

User: admin 

password: (admin password from earlier, generated in terminal) - Should be in notes. 

Next, on the dashboard I go to New Item, enter a name, select pipeline type and click OK.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2023.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2024.png)

Now I scroll down to the pipeline script and this is where I will paste my visual studio code content. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2025.png)

Before I get started with the pipeline, in a new tab in the terminal I run `docker container ls` 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2026.png)

Copy the container ID 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2027.png)

Then I run this command - `docker exec -it -u root <containerID> /bin/bash` 

This command is going log me in to that container, give me an interactive terminal so I can type and get the output, login as root user and the command we run is /bin/bash. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2028.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2029.png)

Now I run `apt-get update` 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2030.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2031.png)

Once done updating, I run `apt-get install maven` and when asked, type `y` to continue.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2032.png)

***Information about Jenkins is persisted, so for whatever reason it goes down, I need to reinstall maven with the command above.*** 

After Maven is installed, I type `exit` in the terminal and close the tab. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2033.png)

- **Install bracket colourizer for vscode, this will help with placing code in the right places inside the Jenkinsfile.**

Back in the Jenkinsfile I created in VScode, I put a pipeline statement, an agent, tools bracket including maven, with a clean up stage with deleteDir(Recursively delete the current directory from the workspace), with a clone repo stage that runs sh(bash-shell) and paste in the github repo url. Then I add another stage with a dir step. I need to work inside this step, I put the project name in dash form and make another sh called mvn clean install. Finally after that, I add a test stage to make sure the application outputs what it expects, which is hello world. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2034.png)

Now I copy all the code from the Jenkinsfile, go back to jenkins, refresh the tab and paste the code in the pipeline script on the build triggers page and hit Save. 

I click build now on the left of the Jenkins dashboard.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2035.png)

View of the console output once done building pipeline. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2036.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2037.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2038.png)

I can even see the logs of each particular stage of the build by hovering over the small table that appears. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2039.png)

**Quick Note on Replay:** 

Replay allows me to go ahead and edit the pipeline script for experimental with changes in here, and then once I’ve got it working, I can keep failing as much times as I need. This is really useful for debugging and making commits afterwards. 

But if the for whatever reason the job fails again, then it shows up in the red, usually because of some sort os syntax error and Jenkins will display an error page. 

So rather than pushing something up to github again for changes, waiting for Jenkins to build, I can click replay, make a minor tweak and I’m happy with the changes, I can go ahead and commit.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2040.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2041.png)

## GitHub Jenkins:

I open the Jenkins folder and head into the Jenkinsfile in the repository I forked over on github. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2042.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2043.png)

I click on the pencil icon on the top right to edit the file to have just agent any at the top with no docker or args. I don’t need a custom stage to pull down or clone the repository, because when using github, it will automatically pull it down for us. Added tools block including maven just incase of the ‘mvn not found’ error.

(example in image below)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2044.png)

 

Then I scroll down to commit changes. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2045.png)

I head back to the main view of the repository and copy the clone https url.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2046.png)

I go back to Jenkins and create a new pipeline and call it GitHub Pipeline.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2047.png)

After clicking OK, I scroll down to pipeline script drop down menu and select pipeline script from SCM, with the SCM being Git and pasting the git url underneath. The script path located at the bottom I put jenkins/Jenkinsfile because in the forked repository the Jenkinsfile is under a jenkins folder. Click Save afterwards.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2048.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2049.png)

Once I’m back in the Jenkins dashboard, I click ‘Build Now’.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2050.png)

Console Output: 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2051.png)

Stage View:

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2052.png)

Polling SCM:

Jenkins is going to check on your platform from github or bitbucket and it going to check for any changes, and if it detects a change, it will start building the job. 

In the pipeline dashboard, I head over the configure and scroll down to build triggers. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2053.png)

After that, I open another tab for crontab.guru and set a cronjob. I set the time for the cronjob to activate every 2 minutes. 

On Jenkins Poll SCM I set the schedule to activation 2 minutes and ? seconds left over by typing H/2****

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2054.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2055.png)

Then I head back to github and go into my Jenkinsfile and edit. 

I create another stage at the bottom underneath stage ‘deliver’ and call it ‘Complete’ and underneath put an echo saying ‘Job Complete!’

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2056.png)

After I add a commit at the bottom. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2057.png)

Now I refresh my Jenkins tab and wait for 2 mins roughly for another job to start building. 

After 2 mins the build was successful, as seen on the stage view even showing my commits under the runtime for the pipeline. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2058.png)

Setting up a MultiBranch Pipeline:

First thing I do head back to the Jenkins dashboard and create a new item, select multi-branch pipeline and give it a name. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2059.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2060.png)

On the next page, I select git as branch source 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2061.png)

Paste in the github repo url 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2062.png)

Put the correct path for the script 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2063.png)

Set scan pipeline triggers on 2 mins, to give enough time for the developers. After that I click Save. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2064.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2065.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2066.png)

I head back to github tab and click to master branch drop down menu (left-hand side), search `newpipeline` and click on `create branch newpipeline`  

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2067.png)

Now we can see I have a new branch. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2068.png)

Back on Jenkins in 2 minutes, it is going to scan again.

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2069.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2070.png)

Now that i’m on a new branch, I can go ahead and edit the Jenkinsfile for any future changes much more easier. 

Example I will so is that I can go back to the Jenkinsfile on github, edit the file and remove the ‘complete’ stage and make a comment afterwards. 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2071.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2072.png)

Go back to multi-branch and select `Scan multi-branch pipeline` 

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2073.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2074.png)

![Untitled]((Jenkins)%20Jenkins%20CI%20CD%20Pipelines%20-%20Automation%20bui%2081b95783e0454af7a69ce113d17b3764/Untitled%2075.png)