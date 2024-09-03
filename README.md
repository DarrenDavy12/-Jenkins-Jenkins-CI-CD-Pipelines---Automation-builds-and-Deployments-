# -Notes-Jenkins-CI-CD-Pipelines-Automation-builds-and-Deployments

This is just notes I took on setting up a CI/CD pipeline using Jenkins.
So for this little project is about building a pipeline on Jenkins which involves continuous integration and continuous delivery/deployment. 

To start off the building process I must first setup Jenkins for the pipeline, so I connect to the Jenkins running off a Docker container using port 8080 which comes from Jenkins. Storing the password for my Jenkins server on my local machine once running the docker run Jenkins on port 8080 command. 

Entering Jenkins using that authentication password and using suggested plugins. Once filling in the admin credentials I use the URL given and paste it inside another tab on the browser. 
I create the first job which is a freestyle project, executing shell for the build step with a simple echo command. Afterwards I clicked build and the pipeline started building, meanwhile I headed into the console output to see the build happening in real time. 

Once done, I head over to my VSCode on my local machine and make new folder called Jenkins and inside that I create a Jenkinsfile and this is where my pipeline will be created. 
Then I head back to my Jenkins tab and make a pipeline. Inside the pipeline I add a script, but before I do that I must run commands for Docker to allow me to log into a container as root. Updated the container and install maven and then exit the container and close tab on terminal.

Back on VSCode I type up my Jenkinsfile that includes agents, stages and the maven tool, while using Jenkins pipeline syntax docs online website. I also added a little stage saying complete wrapped in an echo statement. I added this because I want to show proof when I created the multi-branch pipeline for the scanning feature and to understand that it can benefit last second changes made to the Jenkinsfile.
Once that was done I copied the finished code from my Jenkinsfile into the pipeline script box under build triggers on my Jenkins tab. I click build again and go the console output and when finish I take a look at the logs back on the Jenkins dashboard. 
I go through the benefits of Jenkins replay feature as well. 

I forked over a git repo from the course lecture and headed into the Jenkisnfile and edited the file to just have the tool being used which is maven, with not docker cmds or args. I explain that I don’t need a custom stage to pull down or clone the repo GitHub will already do that for me. After that I commit changes. 
Once I'd cloned the edited repo, I headed back over to Jenkins and to make another pipeline called GitHub pipeline. On the next page I scrolled down to script and in the drop down menu, selected script form SCM (source control management). Added the path of where the Jenkinsfile is on the forked repo and then clicked build now. 

Afterwards I check for any changes and if it detects a change, it will start building the job automatically using polling, I used the crontab guru site and once editing the Jenkinsfile on github again to add deliver stage I commit changes. 
Refreshing tab and waited a couple mins for Jenkins to automatically start building another job. 
Also I covered steps on making a Muliti-branch pipeline on Jenkins, with Git as the branch source, including the Jenkinsfile script path again. Enabling scan multi-branch pipeline triggers for 2 minutes. 
Back on Github on the same forked repo, I clicked on the drop down menu search newpipeline and it was up. I went back to Jenkins and Jenkins automatically started scanning after round 2 minutes has passed.
I did this so making changes to the Jenkinsfile on a new branch makes edits and commits more easier. removed that little complete stage. 

Finally I headed back to Jenkins and clicked on scan multi-branch pipeline and it started scanning again and once done the stage view showed my latest commit change, ‘removed complete stage’ which was the stage I mentioned adding earlier.
