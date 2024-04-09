# Create Web App from Docker Container in Azure

**There are 5 objectives with this lab:**
* Start Cloud Shell
* Set Resource Variables in Cloud Shell
* Create a New Container Registry
* Build an Image and Push to ACR
* Create and Deploy a New Web App


## Start Cloud Shell

I want to start this lab off by saying I didn't know how to do this lab at all so I resorted to watching the walkthrough and go through the text guide. All the commands are sourced from the walkthrough but I chose to modify them and explain each part of the command so show full understanding of whats happening. So with that being said, lets start this lab!

In the first part of the lab, we'll need to get the Azure Cloud Shell up and running. We've done this plenty of times so no walkthrough here. Use Bash and make sure the location matches the location of the storage account in your resource group (RG) though. 

Once your Cloud Shell is up,  that completes the first objective of this lab! On to objective 2. 

## Set Resource Variables in Cloud Shell

For the second portion of this lab, we're going to the container registry using Azure Cloud Registry (ACR). So the first thing I did was create a variable for both my resource group and the name of my container registry since we'll need to refer to these values in the following commands. It's only three commands but this just makes it easier to not make mistakes. 

![Image](AzureCreateACR1.png)




That completes the second objective. Lets move to the 3rd one. 

## Create a New Container Registry

Now, we have to build the custom image and push it to the ACR. First thing we need to do is go to the `clouddrive` directory in the Azure Cloud Shell. Why do we have to go here? I'm not exactly sure but here's some more background on this directory:



![Image](AzureCreateACR4.png)




Now we're done with Objective 3. Lets move on to the final objective. 

## Create and Deploy a New Web App

Now, lets actually run the repository that we built. We'll use the command `az acr run --registry $ACR --cmd '$Registry/evtest-example:v1.0.0' /dev/null` to do that and per usual, lets break it down:


## Build an Image and Push to ACR

Lab completed!

## Personal Notes

I also didn't understand this lab the first time I did it and had to look at the guide BUT after going through the last ACR lab meticulously, I understand majority of what's happening now. The Azure App Services is a PaaS that allows you to deploy applications without dealing with the underlying infrastructure. In our case, we're doing Web Apps so it allows us to create the contents of a web page (HTML and CSS) and be given a URL without having to do a bunch of extra work (DNS, networking, SSL, etc). With that being said, how does a container make any of this easier? 

Well, the source of this web page is a `home.pug` file that has all of our website text in a suitable HTML and CSS format. It uses Express and something else to make this website easy to deploy. Now, this home.pug file and extension is run using node.js. The file that runs this code on GitHub is called app.js. Someone created these files for this lab. The app.js file runs off of the node.js and npm (node.js package manager?) softwares. How do we get those softwares? We get them through our container that is running a Linux image (CentOS) that can run those two softwares. How do we know which versions of those node.js and npm softwares to run? We have a package.json file that the Dockerfile references when it's being told to install node.js and npm. 

Now do I know all of the specifics and what each part of the app.js and home.pug files mean? I don't understand the syntax. I don't understand all of the Docker syntax. But these all work together to easily create a website. 

Recap, the Web App can host the docker file which is instructed to install an OS (CentOS) that can handle the instruced node.js and npm packages that can run the app.js file which is able to efficiently read the home.pug file. Thats the  point of this lab. 
