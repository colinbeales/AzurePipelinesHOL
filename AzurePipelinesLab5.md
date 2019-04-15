# Lab 5: Add approvals to the pipeline
When we deployed our release pipeline from the last lab it deployed to each environment (Dev, QA and Production) one by one without any pausing. It is common to want some kind of sign-off in-between stages where validation can be done and signe-off against before deployment progresses to the following stage. In this lab we will put in such a sign-off.

## Task 1: Adding our approvals

1. Head to menus on the left hand side and select the releases icon under the pipelines icon (both are rockets). Click "Edit" to edit our release pipeline.

<img src="images/Lab5_1.png" width="624"/>

2. On the visual canvas of our pipelines there are icons on each stage to the left and right hand side. These icons allow us to setup pre (left) and post (right) conditions which approvals are part of. We'll setup on of each for our pipeline so lets start with a post deployment condition by clicking the icon on the right side of the Dev. Post deployment condition means Dev will deploy and then we will be required to sign-off the pipeline moves to the next QA stage. Click the icon now.
   
<img src="images/Lab5_2.png" width="624"/>

3. In the post deployment conditions screen firstly "Enable" post deployment approvals. You will then be asked for a user or a group (or both) to sign-off this approval. In this instance we'll say anyone in our team. The easiest way to do this is to look at our project name (in green on the below image) and start typing this into the approvers field and selecting the team from the dropdown. Once this is done you can close the post deployment conditions dialog.

<img src="images/Lab5_3.png" width="624"/>

4. Back at the visual canvas you can see (marked in green on the image below) that a small tick has appeared on the icon denoting we have a post deployment condition set for the Dev stage. Lets setup a pre-deployment condition for production so a sign-off is required before a production deployment takes place. To do this click the icons to the left of the Production stage.
   
<img src="images/Lab5_4.png" width="624"/>

5. There are a few more options on this pre-deployment conditions screen surrounding elements like Triggers, however we need to scroll down and enable "Pre-deployment approvals". This time rather than adding a group as the approver add your name denoting that you and only you can sign-off going into production for this lab scenario. With these set you can exit the pre-deployment conditions dialog.
   
<img src="images/Lab5_5.png" width="624"/>


## Task 2: Turn on continuous deployment.

1. At this point we could trigger a deployment like we've done previously, however to change the scenario at little we are going to enable continuous deployment. This will mean that every new successfull build will trigger our release automatically and be subject to these new approvals we have just created. To do this select the small lightening bolt icon in the top right hand corner of our build artifact.
   
<img src="images/Lab5_6.png" width="624"/>

2. The continuous deployment trigger on the shown dialog just needs to be set to "Enabled" and then we can exit out of the dialog.

<img src="images/Lab5_7.png" width="624"/>

3. Having made our approval changes and our continuous deployment change lets do a quick "Save" to ensure our work is persisted.

<img src="images/Lab5_8.png" width="624"/>

4. As always we need no comment for the Save dialog so just click "OK"

<img src="images/Lab5_9.png" width="424"/>

## Task 3: Execute a continuous deployment release from a new commit.

1. Having made all our changes we want to trigger a new continuous integration build (CI) which will in turn if successful trigger a continuous deployment release (CD). First of all lets go make a code change from Azure Repos so head to the menu on the left for Azure Repos select the sub-menu "Files"

<img src="images/Lab5_10.png" width="424"/>

2. On the left hand side a tree-control structure allows us to navigate the folders and files in the repo. Drill down into the "SimpleDotNetCoreApp" folder, then into "Views" and into the "Home" directory. Inside of "Home" select the "Index.chtml" file and then select "Edit" so we can make a change to this source file.

<img src="images/Lab5_11.png" width="624"/>

3. We can now make a nice visible change into our view so we'll know that our code has been modified and deployed later. Append to the H1 tag the word "Modified". With this done click "Commit" to add this change into our repo.
   
<img src="images/Lab5_12.png" width="624"/>

4. The commit dialog need no change of comment or branch so just click "Commit" and a new change will be persisted to the Repo, which in turn will trigger a CI build and a new release triggered by continuous deployment.
<img src="images/Lab5_13.png" width="624"/>

5. Lets check our build is executing by heading back to the builds area of pipelines using the menus of the left and selecting the sub-menu option of "Builds".
   
<img src="images/Lab5_14.png" width="424"/>

6. The builds screen should show our build and the new build either executing or completed. The image below in green shows the area to check which has a blue icon if the build is executing and a green tick once the build is complete. Wait until this has a green tick and then we'll know our build was succesful and our continuous deloy release will have triggered.
   
<img src="images/Lab5_15.png" width="624"/>

7. To check on our continuous deployment release lets head to the "Releases" area from the menu and sub-menu on the left hand side (the small rocket).
   
<img src="images/Lab5_16.png" width="50"/>

8. The releases screen should show the progress of the deployment out to the Dev stage of our pipeline. Once Dev has deployed our post-deployment approval will be required before anything progresses further. You will see a blue clock icon when an approval is required. It's worth noting that a notification email would be sent at this point, but we can respond directly from this screen by clicking the "Dev" stage with the blue clock icon.
   
<img src="images/Lab5_17.png" width="624"/>

9. (Optional step) Before we sign-off our release it may make sense to actually check that we have successful deployment of the modified code. Create a new borwser tab and head to the "https://uniquewebappnamedev.azurewebsites.net" url. Remember "uniquewebappnamedev" will be different for your instance to the value you input to the variable for WebAppName in the release pipeline for the Dev stage. You should see something like the below image with the area in green showing the "Modified" change.
    
<img src="images/Lab5_18.png" width="624"/>

10. We are now ready to do our approval so click "Approve".
    
<img src="images/Lab5_19.png" width="624"/>

11. The post-deployment approval screen allows us to make a comment that would be available at a later date for auditing reasons. We don't need to fill this out today so just click "Approve".
    
<img src="images/Lab5_20.png" width="624"/>

12. Our approval is now done, so lets exit from the post-deployment approvals dialog.
    
<img src="images/Lab5_21.png" width="624"/>
<img src="images/Lab5_22.png" width="624"/>
<img src="images/Lab5_23.png" width="624"/>
<img src="images/Lab5_24.png" width="624"/>
<img src="images/Lab5_25.png" width="624"/>
<img src="images/Lab5_26.png" width="624"/>
<img src="images/Lab5_27.png" width="624"/>
<img src="images/Lab5_28.png" width="624"/>



## Task 2: Execute a release on using the new release pipeline

1. Let's kick off a new release on our pipeline by selecting "Create release" from the "Release" dropdown.
  
 [<- Lab 4: Add additional stages](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab4.md) | [Lab 6: Create a CI build for a docker container ->](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab6.md)
