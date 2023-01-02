# (Jenkins) Jenkins CI/CD Pipelines - Automation builds and Deployments

## Setup:

First inside the terminal, I ran this command to get Jenkins up and running in Docker.

We are going to expose two ports 8080:8080 but we going to connect to 50000 which is used internally by Jenkins. While creating a volume on a local machine and Docker take care of this for us. It’s a folder to store all the information for Jenkins. It is useful if for whatever reason, a docker container stops. We can re-run it using this command and we’ll have all our information saved. 

cmd: `docker run -p 8080:8080 -p 50000:50000 --restart=on-failure -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11`

![Untitled](https://user-images.githubusercontent.com/42151912/210248725-b1e8ccbb-aee3-4c76-ab62-ab3abd7eb682.png)


Copied the given password and entered it in terminal for further installation. (Store it somewhere safe on local machine) 

![Untitled 1](https://user-images.githubusercontent.com/42151912/210248761-c305e62c-89d0-46bf-8b89-a0b6218b4da9.png)

![Untitled 2](https://user-images.githubusercontent.com/42151912/210248778-3beb3008-5c8a-4f5e-bbef-57a8297a6f06.png)

![Untitled 3](https://user-images.githubusercontent.com/42151912/210248799-410934bf-9781-4196-b3b1-7d0b1d26e024.png)


Once the installation is complete, I went to my browser, in a new tab and in the url typed [localhost:8080](http://localhost:8080) and I get this page, which means we have connected to Jenkins port 8080. 

![Untitled 4](https://user-images.githubusercontent.com/42151912/210248824-e1fc1d96-041c-46ae-8498-a307de571c14.png)


Then I entered the password I copied from the Jenkins command  I ran earlier and hit continue. 

![Untitled 5](https://user-images.githubusercontent.com/42151912/210248844-3040d499-bc95-4382-9e36-13fd44cc8d21.png)


Selected the install suggested plugins.

![Untitled 6](https://user-images.githubusercontent.com/42151912/210248862-6eb4fe7b-6754-495c-99f6-14b7a6ac1cfb.png)


Waited until all the plugins are installed. 

![Untitled 7](https://user-images.githubusercontent.com/42151912/210248882-9aef73d8-63dc-4545-a4fe-aca4b4d892aa.png)


Clicked skip and continue as admin at the bottom. 

![Untitled 8](https://user-images.githubusercontent.com/42151912/210248892-7aa135ee-2f38-42a0-aae4-425003599e09.png)


Then I clicked Save and Finish. On the next page I clicked start using Jenkins.

![Untitled 9](https://user-images.githubusercontent.com/42151912/210248908-147cb30e-23a1-4ce9-984f-493cf3f545fc.png)

![Untitled 10](https://user-images.githubusercontent.com/42151912/210248917-0b42c5df-bd04-478c-86c2-2b0d4c38e4d3.png)


Now I have Jenkins installed.

![Untitled 11](https://user-images.githubusercontent.com/42151912/210248936-adfde660-99f6-4c57-9378-ac4ea516d407.png)


## Create New Jobs:

I go to create a job.

![Untitled 12](https://user-images.githubusercontent.com/42151912/210249010-df9f3fd8-8298-448a-9021-ad06564ca288.png)

- Freestyle project - most common, it’s like a blank slate, create whatever we want
- Pipeline - Create declarative pipelines, Continuous Integration and Continuous Deployment
- Multi-configuration project - Not used as often, run same jobs but with slightly different parameters
- Folder - Organize our jobs, folder for testing, folder for build
- MultiBranch Pipeline - Most powerful pipeline, jobs been setup can hold every single branch of that repo, we don’t have to set another job when part of a team, mulit-branch pipeline will take care about for you
- Organization Folder - Similar to multibranch but it scans for repos from Source control Managers - Github etc


![Untitled 13](https://user-images.githubusercontent.com/42151912/210249021-dfa51378-342a-45f9-87f1-2572a2866622.png)


Moving on, I gave a name for the project and selected freestyle project and clicked ok. 

![Untitled 14](https://user-images.githubusercontent.com/42151912/210249035-afe295c4-f22f-4f1f-a855-669d070debe7.png)


Next I scroll down to the bottom and click the Add build step and selected Execute shell.

![Untitled 15](https://user-images.githubusercontent.com/42151912/210249091-0f1f887d-ca95-4f6c-957b-b1f5df2bcccc.png)


Then I added this command (in image below) inside the shell which has popped up and afterwards I hit Save.

![Untitled 16](https://user-images.githubusercontent.com/42151912/210249105-84297649-ec11-4167-8e40-74854f374644.png)


Once we are shown back to the dashboard and click build now. 

![Untitled 17](https://user-images.githubusercontent.com/42151912/210249125-9f867bd9-0511-4b59-b07e-7d5c6d807b0a.png)


At the bottom, I click on #1 

![Untitled 18](https://user-images.githubusercontent.com/42151912/210249145-200dfd5c-4884-461f-8e54-9ec6c9676365.png)


I go to console output and see the command message I wrote earlier and my little Jenkins job is up and running. 

![Untitled 19](https://user-images.githubusercontent.com/42151912/210249325-c495d37a-5a98-42ec-98a0-00b75bd9cbcb.png)


## Pipelines:

First I got into VScode and click open folder and make a new folder called `Jenkins` and open it up in VScode. 

![Untitled 20](https://user-images.githubusercontent.com/42151912/210249339-2d18c4fe-cc54-4c5f-ae43-27bd0d34e341.png)

![Untitled 21](https://user-images.githubusercontent.com/42151912/210251242-18ef374c-f8e7-41a2-a777-8d545b3e53af.png)


I create a new file inside the folder called `Jenkinsfile` 


![Untitled 22](https://user-images.githubusercontent.com/42151912/210249388-5f99f74a-3134-43be-9b0e-84845cafc946.png)

I create my pipeline here, and then copy and paste it inside the Jenkins job. 

If I logged out of Jenkins the credentials I must use are:

User: admin 

password: (admin password from earlier, generated in terminal) - Should be in notes. 

Next, on the dashboard I go to New Item, enter a name, select pipeline type and click OK.


![Untitled 23](https://user-images.githubusercontent.com/42151912/210249412-3fe00409-7da0-4e41-85e6-a8034caa8e8c.png)


Now I scroll down to the pipeline script and this is where I will paste my visual studio code content. 

![Untitled 24](https://user-images.githubusercontent.com/42151912/210249426-9a322358-905d-4ddd-bac5-cd863ee8109a.png)

![Untitled 25](https://user-images.githubusercontent.com/42151912/210249437-eb9903df-ea18-49f1-9049-a2171ca0ee87.png)


Before I get started with the pipeline, in a new tab in the terminal I run `docker container ls` 


![Untitled 26](https://user-images.githubusercontent.com/42151912/210249453-27b8cd6a-1d56-4068-875b-78d1e103bf23.png)


Copy the container ID 


![Untitled 27](https://user-images.githubusercontent.com/42151912/210249476-ebd07f05-a6d1-42f3-b5e9-e18403581955.png)


Then I run this command - `docker exec -it -u root <containerID> /bin/bash` 

This command is going log me in to that container, give me an interactive terminal so I can type and get the output, login as root user and the command we run is /bin/bash. 

![Untitled 28](https://user-images.githubusercontent.com/42151912/210249491-0237308b-b70e-47ba-8f9e-b5bab7fb6112.png)

![Untitled 29](https://user-images.githubusercontent.com/42151912/210251049-0b11be5e-27fa-4a76-9672-c84cdb05f2fe.png)


Now I run `apt-get update` 

![Untitled 30](https://user-images.githubusercontent.com/42151912/210249530-04454e2c-6468-41bb-9c5d-07c126af8fc5.png)

![Untitled 31](https://user-images.githubusercontent.com/42151912/210250996-c737c82c-f151-4322-9ee3-35218276cb1c.png)


Once done updating, I run `apt-get install maven` and when asked, type `y` to continue.

![Untitled 32](https://user-images.githubusercontent.com/42151912/210250938-9948e171-f0ad-43b5-a71c-3c58f9fad1d3.png)


***Information about Jenkins is persisted, so for whatever reason it goes down, I need to reinstall maven with the command above.*** 

After Maven is installed, I type `exit` in the terminal and close the tab. 

![Untitled 33](https://user-images.githubusercontent.com/42151912/210249598-09755d0e-ad2b-4101-b958-ce23b39adbe6.png)


- **Install bracket colourizer for vscode, this will help with placing code in the right places inside the Jenkinsfile.**

Back in the Jenkinsfile I created in VScode, I put a pipeline statement, an agent, tools bracket including maven, with a clean up stage with deleteDir(Recursively delete the current directory from the workspace), with a clone repo stage that runs sh(bash-shell) and paste in the github repo url. Then I add another stage with a dir step. I needed to work inside this step, I put the project name in dash form and make another sh called mvn clean install. Finally after that, I added a test stage to make sure the application output is hello world. 


![Untitled 34](https://user-images.githubusercontent.com/42151912/210250687-998e3b94-7e95-41ff-a2f7-7971060433f0.png)

Now I copy all the code from the Jenkinsfile, go back to jenkins, refresh the tab and paste the code in the pipeline script on the build triggers page and hit Save. 


I clicked build now on the left of the Jenkins dashboard.

![Untitled 35](https://user-images.githubusercontent.com/42151912/210249691-a2e22b85-17c3-4076-aa25-966699349674.png)

Viewed the console output once done building pipeline. 

![Untitled 36](https://user-images.githubusercontent.com/42151912/210250444-f7161e17-01de-4db4-973e-cc8c52ae26d7.png)

![Untitled 37](https://user-images.githubusercontent.com/42151912/210250463-cb49c312-a346-49d7-8581-35a3049d14b8.png)


I can even see the logs of each particular stage of the build by hovering over the small table that appears. 

![Untitled 38](https://user-images.githubusercontent.com/42151912/210251342-6a1e57fa-21f1-4b45-b1fb-ce6b84f374d2.png)


**Quick Note on Replay:** 

Replay allows me to go ahead and edit the pipeline script for experimental with changes in here, and then once I’ve got it working, I can keep failing as much times as I need. This is really useful for debugging and making commits afterwards. 

But if the for whatever reason the job fails again, then it shows up in the red, usually because of some sort os syntax error and Jenkins will display an error page. 

So rather than pushing something up to github again for changes, waiting for Jenkins to build, I can click replay, make a minor tweak and I’m happy with the changes, I can go ahead and commit.

![Untitled 39](https://user-images.githubusercontent.com/42151912/210251370-92d00307-8908-4c64-ae53-c0c2ee37fe03.png)

![Untitled 40](https://user-images.githubusercontent.com/42151912/210251378-747b3abb-66be-4088-9367-ab9c6aacf393.png)


## GitHub Jenkins:

I open the Jenkins folder and head into the Jenkinsfile in the repository I forked over on github. 

![Untitled 41](https://user-images.githubusercontent.com/42151912/210251394-a8a38f4e-46e0-4fe4-97e8-d847391d7306.png)

![Untitled 42](https://user-images.githubusercontent.com/42151912/210251407-f27875d6-d744-4340-991c-65dd4657e945.png)


I click on the pencil icon on the top right to edit the file to have just agent any at the top with no docker or args. I don’t need a custom stage to pull down or clone the repository, because when using github, it will automatically pull it down for us. Added tools block including maven just incase of the ‘mvn not found’ error.

(example in image below)


 ![Untitled 43](https://user-images.githubusercontent.com/42151912/210251425-9d3839c6-4f36-40c9-b9db-1e69a23f9059.png)


Then I scroll down to commit changes. 

![Untitled 44](https://user-images.githubusercontent.com/42151912/210251437-0cea24bd-cb8d-49e9-9c8f-2fe43e631c4e.png)


I head back to the main view of the repository and copy the clone https url.

![Untitled 45](https://user-images.githubusercontent.com/42151912/210251458-c4e6b6ec-1313-44e1-9c14-adf5fded7ffd.png)


I go back to Jenkins and create a new pipeline and call it GitHub Pipeline.

![Untitled 46](https://user-images.githubusercontent.com/42151912/210251478-be2a716e-fac6-4c15-8760-7d7cf23bf014.png)


After clicking OK, I scroll down to pipeline script drop down menu and select pipeline script from SCM, with the SCM being Git and pasting the git url underneath. The script path located at the bottom I put jenkins/Jenkinsfile because in the forked repository the Jenkinsfile is under a jenkins folder. Click Save afterwards.

![Untitled 47](https://user-images.githubusercontent.com/42151912/210251492-cca05445-a38f-455c-b663-9fba84067de7.png)

![Untitled 49](https://user-images.githubusercontent.com/42151912/210251502-1b3de0fc-6ac4-4200-b00e-43390fe0a124.png)


Once I’m back in the Jenkins dashboard, I click ‘Build Now’.

![Untitled 50](https://user-images.githubusercontent.com/42151912/210251515-3be88235-215b-4ede-a480-8b66203f8379.png)


Console Output: 

![Untitled 51](https://user-images.githubusercontent.com/42151912/210251543-d35bf50a-74b4-47d8-af35-226645739cfd.png)


Stage View:

![Untitled 52](https://user-images.githubusercontent.com/42151912/210251567-9f1c9ead-7633-42e5-8964-9f673b3e524a.png)


Polling SCM:

Jenkins is going to check on your platform from github or bitbucket and it going to check for any changes, and if it detects a change, it will start building the job. 

In the pipeline dashboard, I head over the configure and scroll down to build triggers. 

![Untitled 53](https://user-images.githubusercontent.com/42151912/210251583-005c4142-4370-49f8-81bb-0d3b618bf94e.png)


After that, I open another tab for crontab.guru and set a cronjob. I set the time for the cronjob to activate every 2 minutes. 

On Jenkins Poll SCM I set the schedule to activation 2 minutes and ? seconds left over by typing H/2****

![Untitled 54](https://user-images.githubusercontent.com/42151912/210251636-5d8135a3-101f-4bd1-a12d-f65b722ab907.png)

![Untitled 55](https://user-images.githubusercontent.com/42151912/210251649-a185bee1-726b-458f-92dd-133d446e5c67.png)


Then I head back to github and go into my Jenkinsfile and edit. 

I create another stage at the bottom underneath stage ‘deliver’ and call it ‘Complete’ and underneath put an echo saying ‘Job Complete!’

![Untitled 56](https://user-images.githubusercontent.com/42151912/210251659-c4904fb1-16cb-4ab3-ba7c-d474d6c868b7.png)


After I add a commit at the bottom. 

![Untitled 57](https://user-images.githubusercontent.com/42151912/210251678-fca90059-6856-496c-8ff0-46f625de8112.png)


Now I refresh my Jenkins tab and wait for 2 mins roughly for another job to start building. 

After 2 mins the build was successful, as seen on the stage view even showing my commits under the runtime for the pipeline. 

![Untitled 58](https://user-images.githubusercontent.com/42151912/210251702-d8754ba2-287a-4083-8bc7-7f9a638126e4.png)


Setting up a MultiBranch Pipeline:

First thing I do head back to the Jenkins dashboard and create a new item, select multi-branch pipeline and give it a name. 

![Untitled 59](https://user-images.githubusercontent.com/42151912/210251718-4a0da84a-0baa-448a-828e-f97cd89cd72b.png)

![Untitled 60](https://user-images.githubusercontent.com/42151912/210251732-47bd2d05-90ed-4153-9176-079a3336ef98.png)


On the next page, I select git as branch source 

![Untitled 61](https://user-images.githubusercontent.com/42151912/210251866-5a315ba4-e734-4d2d-aad1-65a520a1cdb2.png)


Paste in the github repo url 

![Untitled 62](https://user-images.githubusercontent.com/42151912/210251888-bb253ceb-36cb-4ef4-938d-67af1697c265.png)


Put the correct path for the script 

![Untitled 63](https://user-images.githubusercontent.com/42151912/210251907-bafd2e1f-6cee-4f5d-9639-003d7a7224cd.png)


Set scan pipeline triggers on 2 mins, to give enough time for the developers. After that I click Save. 

![Untitled 64](https://user-images.githubusercontent.com/42151912/210251922-17ef7bcf-1a94-49d3-8406-4607a13ecaba.png)

![Untitled 65](https://user-images.githubusercontent.com/42151912/210251937-6fcbe838-8946-4844-8b5d-0fff9be3b45d.png)

![Untitled 66](https://user-images.githubusercontent.com/42151912/210251940-1ceaa80b-e5e2-40a9-b85b-75f0544a5ad4.png)


I head back to github tab and click to master branch drop down menu (left-hand side), search `newpipeline` and click on `create branch newpipeline`  

![Untitled 67](https://user-images.githubusercontent.com/42151912/210251947-fd9a08d7-6f4d-48b8-8ddf-8b943c2803b0.png)


Now we can see I have a new branch. 

![Untitled 68](https://user-images.githubusercontent.com/42151912/210251957-6260ded0-8a6d-4267-b5ce-f541c0cc6656.png)


Back on Jenkins in 2 minutes, it is going to scan again.

![Untitled 69](https://user-images.githubusercontent.com/42151912/210251976-8c581a41-0bbb-444b-923d-068455261aa2.png)

![Untitled 70](https://user-images.githubusercontent.com/42151912/210252021-2079f597-22a5-429f-8ae7-8311f5e05a07.png)


Now that i’m on a new branch, I can go ahead and edit the Jenkinsfile for any future changes much more easier. 

Example I will so is that I can go back to the Jenkinsfile on github, edit the file and remove the ‘complete’ stage and make a comment afterwards. 

![Untitled 71](https://user-images.githubusercontent.com/42151912/210252039-796b268d-696e-4afe-9b2d-de7db6903089.png)

![Untitled 72](https://user-images.githubusercontent.com/42151912/210252054-68187a9d-6778-4b78-8a7f-42ec85cf7e88.png)


Go back to multi-branch and select `Scan multi-branch pipeline` 

![Untitled 73](https://user-images.githubusercontent.com/42151912/210252070-727b25cd-8570-4b1e-8d0e-29d9dec654d9.png)

![Untitled 74](https://user-images.githubusercontent.com/42151912/210252083-3730766a-084b-4244-9c41-e77e7002a638.png)

![Untitled 75](https://user-images.githubusercontent.com/42151912/210252092-90dd0932-36e6-49a8-99ac-c66977bf59d4.png)
