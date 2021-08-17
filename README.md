# Node JS App Deployment Using Jenkins

## Depolyment using Jenkins UI Tool (freestyle project)
This readme contains the stepwise instruction to build and deploy a node js app using jenkins, git, docker

1. Install dependency plugins on the Jenkins Machine (Manage Plugins> Add NodeJS> Download and install)
2. We must now install node onto our jenkins (Manage Jenkins> Global Tool Configuration> Add NodeJS)
3. Now create a new job on Jenkins, provide a name to your project and select FreeStyleProject
4. Now we must select the option of source code management to pull the code from git. Provide the https url to jenkins. (Note: If you do not add credentials ensure the git repo is Public)
5. Once you have configured where to pull the code from you need to add build steps, we simply add a shell command to be executed (npm install) To run npm commands we need to add Node and npm/bin to PATH

So far we have pulled the node project from git, run npm install and download the dependency. All done using Jenkins build steps. Now we will package this nodejs application using docker push the image to the docker repository. 

6. Now first we must add the Docker Plugin to Jenkins (Manage plugins> Select CloudBees Docker Build and Publish plugin) Download and install

    NOTE: If jenkins is running in docker, then jenkins must be configured to use docker. A dockergroup must be created and jenkins must be given access to the group. Additional configurations are to be done to configure this jenkins docker to access and use the docker socket. To verify we can go inside our jenkins container and run docker commands.
    
    NOTE: If we were running jenkins outside docker, just installing docker inside our jenkins could have done the same.
7. Now we go back to the jenkins console, add a new build step. "Docker Build and Push". To do this we have to go to hub.docker.com and create an account, add the credentials of the docker account to the jenkins build step. Create a repository on docker-hub and add the repository and account credentials inside the build step. 

Now we have managed to pull our node project from github, build and deploy it in a docker container, push the docker image to our docker-hub account. All of this has been completed through jenkins build steps.

Now we can pull the image from docker-hub on any machine and run the image (it will create a new container). 

## Using Jenkins DSL

1. Add Jobs DSL plugin from the jenkins console. Install and restart.
2. Create a new free style project. Add the project you want to build by providing the git url. Add the job dsl groovy script to your project and specify the location in the jenkins console. 
