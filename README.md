# Azure Pipelines Lab

This set of labs will step through the key elements in setting up and using a build and release pipelines with Azure DevOps.

## Background information

>[What is DevOps?](https://www.visualstudio.com/learn/what-is-devops/)

>[How Microsoft does DevOps](https://www.visualstudio.com/learn/devops-at-microsoft/)

>[Azure Pipelines Documentation](https://docs.microsoft.com/en-gb/azure/devops/pipelines/index?view=azure-devops)

# Lab Details

The labs we will follow today will surround the build and deployment of a simple web application written in C# for .NET Core. Azure pipelines supports any language and can work with technologies accross Windows, Linux and Mac giving scope to write code and create pipelines to suit applications for many different scenarios. The labs chose to use .NET core as we can work with it accross easily accross Windows, Linux and Mac and can deploy the code to any of these platforms or into Linux or Windows container environments. 

The labs are split into 3 main areas. Our first five labs serves as a getting started guide. Taking us through the basic mechanics of working with Azure Pipelines setting up both a build and release pipeline that build our code, deploy our environments using infrastructure-as-code and deploy the code to Azure. Once deployed we will showing the mechanics of deploying to many different environments or stages (i.e. Dev, QA & Production) and putting in place approvals that support your organisational sign-off requirements.

Once we have been through the basic mechanics of the build and release tool we will show some variation in how pipelines can be configured by going into a slighlty more advanced scenario that will take the same code through a process of being built and deployed whilst working with Linux based Docker containers and hosted again within Azure. 

The final section is less guided, providing some ideas that you can take away and work through using your familarity of Azure Pipelines. 

I hope that whether you are familiar with C# and .NET Core or not the lab will still be relevant as the code itself is realitively unimportant as we are aiming to building familiarity of how to work with Azure Pipelines to build and deploy our code whichever language, platform and deployment target we may choose. I hope having completed the lab you will feel confident to tackle creating other pipelines to deploy code from other languages and platforms and deploy either on-premises or to the cloud.

# Overall flow

Setting up a basic pipeline (build-release)
- [Lab 1: Create your Azure DevOps project](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab1.md)
- [Lab 2: Create a continuous integration build](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab2.md)
- [Lab 3: Create a release pipeline](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab3.md)
- [Lab 4: Add additional stages](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab4.md)
- [Lab 5: Add approvals](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab5.md)

Setting up a pipeline working with containers
- [(Advanced) Lab 6: Create a continuous integration build for a docker container](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab6.md)
- [(Advanced) Lab 7: Create a release pipeline to run a container](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab7.md)

Homework
- [(Optional) Hack: Ideas for other pipeline work to extend workshop learning](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab8.md)


Azure DevOps supports any app and doesn't require the use of Visual Studio, .NET or other Microsoft languages or platforms. [Labs that work through implementing DevOps with Node, Java, Eclipse, IntelliJ, Docker and more are available here](https://www.azuredevopslabs.com/).

# Pre-requisites for the lab

For this lab it is assumed that you have:
- An Azure subscription (your own or a [free trial](https://azure.microsoft.com/en-us/free/)).
- An Azure DevOps Organisation [free sign-up](https://dev.azure.com/) but if you don't already have one it will be created in the first lab.

[Lab 1: Create your Azure DevOps project](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab1.md)