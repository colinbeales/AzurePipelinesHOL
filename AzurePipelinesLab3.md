# Lab 3: Creating a release pipeline

## Task 1: Create a new release pipeline

1. Head to menus on the left hand side and select the releases icon under the pipelines icon (both are rockets). On selecting this you will be shown you have no release pipelines, but you can create a new one. Select "New pipeline" to do this.

<img src="images/Lab3_1.png" width="624"/>

2. In a similar style to the build which gave us a choice of pipeline templates, the same is true for a release pipeline. You will be greeted with a host of different templates of application types and platforms that you could use as a scaffold for a release pipeline. Take a second to scroll through the list and take in some of the options available. The one we want to select is "Azure App Service deployment" when you find it select "Apply" 

<img src="images/Lab3_2.png" width="624"/>

3. A release can have many stages in our lab we'll eventually have stages for Dev, QA and Production but for now we'll just have one. Lets name this one "Dev" before we close the dialog.

<img src="images/Lab3_3.png" width="624"/>

4. Our view now will be a visual representation of the Artifacts and stages in our release. As we have no Artifacts we will want this release to be triggered from the successful creation of a build (and the drop that resides within this). Select "Add an artifact" so we can add our build.
   
<img src="images/Lab3_4.png" width="624"/>

5. Artifacts could come from a range of different places, version control, builds and container registries to name a few. In our instance we want our release to come from an artifact created in a Build so make sure "Build" is selected and then in the "Source (Build pipeline)" select the CI build we created in the previous lab. The dialog should expand at this point but you can leave all the defaults as we are happy to use the latest build when we trigger releases by default. Select "Add" and we're done with adding the artifact.
 
<img src="images/Lab3_5.png" width="624"/>

6. Turning our focus to the visual diagram we can see we now have an Artifact which will trigger our Dev stage. We however need to go edit the pipeline for the Dev stage so select the link in the centre (currently should say "1 job, 1 task") which will navigate us to the pipeline for this Dev stage. 

<img src="images/Lab3_6.png" width="624"/>

7. This should look pretty familiar now. The release pipeline is setup very similarly to our build pipeline, with agent jobs hosting tasks. In this instance the scaffold template we picked simply put one agent job in place with one single "Deploy Azure App Service" task within it. We'll add to this later, but for now there are a few settings its letting us know we need attention on. The first of these is the Azure Subscription. Select your subscription from the drop down (it only knows subscriptions you are allowed to access under the user you're logged in against). Once your subscription is selected click the "Authorize" button. The browser will ask pop up a Azure login window now so enter your Azure subscription credentials and the authorization is done. Note: Behind the scenes here in Azure it is setting up a Application in Azure Active Directory that Azure DevOps can use as an identtdy to work with your Azure subscription.

<img src="images/Lab3_7.png" width="624"/>

8. Having authorized we need to provide an "App service name" for the Azure App Service we wish to deploy to. We could hard code this value, but I prefer to use variables as they have more flexibility to set for an entire release (all stages e.g. dev, QA and prod) or have a stage specific value. The format for variables will be familiar to PowerShell users, therefore for a variable called WebAppName we use the "$(WebAppName)" without the quotes. Once this is set select the "Variables" tab where we can set a value for it.
 
<img src="images/Lab3_8.png" width="624"/>

9. Click the "Add" button to add a variable. Then set the "Name" to be "WebAppName" and set a value. The value needs to be unique so use a value of your own here and append the word "Dev" onto the end. Finally set the scope to be "Dev". This means that this value will only be used in the "Dev" stage. Later when we create QA and Production stages we can set different values for each environment. We're done with this screen for now so lets return to the tasks in our pipeline by clicking the "Tasks" tab.

<img src="images/Lab3_9.png" width="624"/>

10. We have a task to deploy an App Service, however the App Service deployment wont work because nothing has created the "App Service" in Azure yet. To do this we could manually go and setup a new App Service in the Azure Portal, however with a DevOps mindset we should prefer to auomate the creation into our pipeline and we use infrastructure-as-code to do this. There are multiple ways to do this in Azure, however for this lab we will use an Azure Resource Management (better known as ARM) template to do this.

    To add a task to the pipeline is the same process we used to add tasks to the build pipeline. Select the "+" on the Run on Agent job, then search the tasks by typing "ARM" into the seachbox. From the search results drag the task into the pipeline into the position before our existing "Deploy App Service" task.

<img src="images/Lab3_10.png" width="624"/>
    
11. There are a number of settings that need changing on this new task so "Select" the Azure Deployment Create task and start setting required properties. First select your Azure Subscription. Because we authorized to work with our Azure subscription previously we should have an Available subscription on our dropdown that we can use and not need to Authenticate like we did previously. Then provide a Resource Group Name. This is up to you but a value like "AzurePipelinesLabGroup" should be very identifiable in your subscription when new resources are created. Then select a region to deploy into, in my case I'm picking "UK South" as its nearest me, but you may wish to pick a closer region if your sitting this lab in another region.
 
<img src="images/Lab3_11.png" width="624"/>

    Scrolling down we have some further settings on this task we need to set, each one by selecting the elipses "..."

<img src="images/Lab3_12.png" width="624"/>

    The template and the template parameters fields can be set by following the dialog to find the ARM json files that describe the resources that we want to create in Azure. You can select "WebSite.json" for the template field and "WebSite.Parameters.json" for the template parameters field.  

<img src="images/Lab3_13.png" width="424"/>

    The override parameters field can be used to override parameters that will be used in the ARM template. This is a chance for us to provide a WebAppName for the App Service that we are going to create. Change the null variable here to the "$(WebAppName)" variable we created earlier. This will mean this task will create the same App Service resource that we deploy to in the next pipeline task.

<img src="images/Lab3_14.png" width="424"/>

12. Before we "Save" our release pipeline lets select the name "New release pipeline" at the top of the screen and give a new more meaningful name like "Pipelines Lab AppService Release". We can now click "Save" to save our release pipeline.

<img src="images/Lab3_15.png" width="624"/>

The Save dialog can have a comment for history, but we'll just sekect "OK" so the save is complete.

<img src="images/Lab3_16.png" width="424"/>

## Task 2: Execute a release on using the new release pipeline

1. Let's kick off a new release by selecting "Create release" from the "Release" dropdown.
  
<img src="images/Lab3_17.png" width="624"/>

2. The Create a new release screen gives a chance to confirm which artifacts will be released, we only have our one build artifacts so we can leave everything as is and click "Create"
    
<img src="images/Lab3_18.png" width="624"/>

3. As we saw with our build we can click the link at the top of the screen to see the progress of our release. Click "Release 1" at the top to see this.
    
<img src="images/Lab3_19.png" width="624"/>

4. If you catch the release in-progress you can click the "In-progress" link to see each step in your pipeline executing in real time. If the release is completed the "In-progress" link is replaced with a "Completed" link that you can click.
        
<img src="images/Lab3_20.png" width="624"/>

5.  Depending on how quickly you clicked through you will either see the steps executing or see all the steps completed meaning our deployment has been successful creating a App Service in a "Dev" environement and deploying our build to this service.
    
<img src="images/Lab3_21.png" width="624"/>

Next we will look to add to this release by adding additional release stages for our QA and production environments.

[<- Lab 2: Create a continuous integration build](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab2.md) | 
[Lab 4: Add additional release stages ->](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab4.md)