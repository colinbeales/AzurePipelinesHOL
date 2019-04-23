# Hack: (Optional) Ideas for extending this lab
There are no more step-by-step exercises to follow, however if you wanted to explore some more of Azure Pipelines here are a few suggestions you might like to extend these labs with:

* Re-create one of the build pipelines done in the labs with a YAML pipeline.
* Add testing of the website after it has deployed. Note: to help with this scenario the code already has some selenium tests in the git repo. Some things you would have to do for these to work.
  * Create your own private agent to run the agent job (required to run the selenium tests).
  * Install Chrome on your private agent machine.
  * Install Webdriver for Chrome ([Webdriver download](https://sites.google.com/a/chromium.org/chromedriver/downloads)). Note: The code expects the chromedriver.exe file to be copied to "C:\tools\selenium".
* Deploy your container to an AKS Kubernetes cluster.
* Deploy this code to a VM either in an Azure VM or an on-premises resource. Note: to do this look at Deployment Groups in Azure Pipelines, [Docs here](https://docs.microsoft.com/en-us/azure/devops/pipelines/release/deployment-groups/?view=azure-devops).  


[<- (Advanced) Lab 7: Create a release pipeline to run a container](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab7.md)
