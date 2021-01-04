 
1.	Navtigate to Jenkins server.
2.	Click New Item.
3.	Enter a name for your project, click Freestyle Project, then OK.
4.	Note: Please do not include a space.
5.	Name this something unique so there are no collisions.
6.	Set up Source Code Management.
7.	Select git.
8.	Enter the URL to your git repository
9.	Setting up Build Triggers
10.	Set up Build.
11.	Add build step Execute Shell.
12.	Enter gcc file name 
13.	Click Save.
If you want a bit more of a challenge consider setting up Webhooks as opposed to polling. A fun Jenkins exercise that can get you thinking.
Set up Embeddable Build Status for Repo

The build status symbol often seen on a Github repository is normally connected to TravisCI or JenkinsCI. We are using JenkinsCI which requires a plugin called Embeddable Build Status. I have already installed it for you. You just need to add the proper information into your README.md file.
1.	Open the README file in a text editor.
2.	Go to the Embeddable Build Status page. The link is found on the main page of the job.
3.	Select the Markdown (with View) protected link and paste it in your README.
4.	Commit your README changes and push to Github.
5.	The change should automatically cause the job to build and after you can go to Github and check your repo. You should see the build status there
Because we selected With View you will be able to click the build status icon which will take you to the Job in Jenkins.
Set up Second Job to Run the Compiled Program
The final step to this demo is to set up a second job that automatically runs after the project builds. This is different than the other job because this will not have a git repository - it doesn't even build anything.
Just a note: In a real-life scenario you wouldn't run a program through a build job just like this because I/O is not possible via this console. There are other tools people use at this step like SeleniumHQ, SonarQube, or a Deployment. The point of this is to show downstream/upstream job relationships.
1.	Create a new Job in Jenkins
2.	Click New Item.
3.	Enter a name for your second job, click Freestyle Project, then OK.
4.	Go immediately to build step and select Execute Shell.
5.	Enter the following Command /var/lib/jenkins/workspace/<the name of your first project>/hello_exec
6.	Save
7.	Set your first job to call the second
8.	Go to your first job and open the Configure page.
9.	Scroll to bottom and add a Post-Build Action. Select Build other projects.
10.	Enter the name of your second job.
11.	Save
12.	Run your first job
13.	Do this by clicking build now on the main page.
14.	After that successfully builds go and check your second job.
15.	You should see it successfully run.
16.	Select a Build Job from History and go to the console log to see your program output. If you program has run there then you successfully set up a basic pipeline.  


