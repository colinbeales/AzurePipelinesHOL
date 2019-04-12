# Azure Pipelines Lab

This set of labs will step through the key elements in setting up and using a build and release pipelines with Azure DevOps.

## Background information

>[What is DevOps?](https://www.visualstudio.com/learn/what-is-devops/)

>[How Microsoft does DevOps](https://www.visualstudio.com/learn/devops-at-microsoft/)

>[Azure Pipelines Documentation](https://docs.microsoft.com/en-gb/azure/devops/pipelines/index?view=azure-devops)

# Overall flow

Setting up a basic pipeline (build-release)
- [Lab 1: Create your Azure DevOps project](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab1.md)
- [Lab 2: Create a continuous integration build](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab2.md)
- [Lab 3: Create a release pipeline](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab3.md)
- [Lab 4: Add additional stages](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab4.md)
- [Lab 5: Add approvals](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab5.md)

Setting up a pipeline working with containers
- [Lab 6: Create a continuous integration build for a docker container](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab6.md)
- [Lab 7: Create a release pipeline to run a container](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab7.md)


Azure DevOps supports any app and doesn't require the use of Visual Studio, .NET or other Microsoft languages or platforms. [Labs that work through implementing DevOps with Node, Java, Eclipse, IntelliJ, Docker and more are available here](https://www.azuredevopslabs.com/).

# Pre-requisites for the lab

For this lab it is assumed that you have:
- An Azure subscription (your own or a [free trial](https://azure.microsoft.com/en-us/free/)).
- An Azure DevOps Organisation [free sign-up](https://dev.azure.com/).
- [Git installed](https://git-scm.com/) in order to commit and push changes to Azure DevOps.
- A text or code editor such as [Visual Studio Code](https://code.visualstudio.com/). 

The lab has been designed so that you don't need to compile and debug locally (in order to reduce dependencies on having specific tools and libraries installed), therefore any editor that can be used to make textual changes to files will be sufficient from Notepad to the Visual Studio IDE. For the lab documentation it is assumed that Visual Studio Code is being used as it's:

- Free (and open source).
- Available for Windows, Mac and Linux.
- A good code editor and has built in Git integration.

You will also need an Azure DevOps organisation but if you don't already have one it will be created in the first lab.

[Lab 1: Create your Azure DevOps project](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab1.md)