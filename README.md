# Node JS App Deployment Using Jenkins

This readme contains the stepwise instruction to build and deploy a node js app using jenkins, git, docker

1. Install dependency plugins on the Jenkins Machine (Manage Plugins> Add NodeJS> Download and install)
2. We must now install node onto our jenkins (Manage Jenkins> Global Tool Configuration> Add NodeJS)
3. Now create a new job on Jenkins, provide a name to your project and select FreeStyleProject
4. Now we must select the option of source code management to pull the code from git. Provide the https url to jenkins. (Note: If you do not add credentials ensure the git repo is Public)
5. Once you have configured where to pull the code from you need to add build steps, we simply add a shell command to be executed (npm install) To run npm commands we need to add Node and npm/bin to PATH

So far we have pulled the node project from git, run npm install and download the dependency. All done using Jenkins build steps. Now we will package this nodejs application using docker push the image to the docker repository. 

6. Now first we must add the Docker Plugin to Jenkins (Manage plugins> Select CloudBees Docker Build and Publish plugin) Download and install

    NOTE: If jenkins is running in docker, then jenkins must be configured to use docker. A dockergroup must be created and jenkins must be given access to the group
7. 
