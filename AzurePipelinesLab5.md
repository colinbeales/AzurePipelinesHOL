# Lab 5: Add approvals to the pipeline
When we deployed our release pipeline from the last lab it deployed to each environment (Dev, QA and Production) one by one without any pausing. It is common to want some kind of sign-off in-between stages where validation can be done and signe-off against before deployment progresses to the following stage. In this lab we will put in such a sign-off.

## Task 1: Adding additional release stages

1. Head to menus on the left hand side and select the releases icon under the pipelines icon (both are rockets). Click "Edit" to edit our release pipeline.

<img src="images/Lab5_1.png" width="624"/>


## Task 2: Execute a release on using the new release pipeline

1. Let's kick off a new release on our pipeline by selecting "Create release" from the "Release" dropdown.
  
 [<- Lab 4: Add additional stages](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab4.md) | [Lab 6: Create a CI build for a docker container ->](https://github.com/colinbeales/AzurePipelinesHOL/blob/master/AzurePipelinesLab6.md)
