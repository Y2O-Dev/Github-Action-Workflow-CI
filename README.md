# Building and Pushing Node.js Docker Image to Amazon ECR using GitHub Actions

## Introduction:
GitHub Actions is a powerful automation platform that allows you to define custom workflows to build, test, and deploy your code. This documentation provides a concise guide on how to use GitHub Actions workflow to push a Docker image to Amazon Elastic Container Registry (ECR).

## Prerequisites:

1. A GitHub repository hosting your Docker project.
2. An Amazon ECR repository to push the Docker image to.
3. AWS credentials with sufficient permissions to push to the ECR repository.

## Step 1: Configure AWS Credentials
To authenticate and access Amazon ECR from GitHub Actions, you need to configure AWS credentials as repository secrets. Follow the following steps:

1. Go to GitHub repository.
2. Click on the "Settings" tab.
In the left sidebar, click on "Secrets".
3. Click on "New repository secret".
4. Enter AWS_ACCESS_KEY_ID as the name and provide your AWS access key ID as the value.
5. Click on "Add secret".
6. Repeat step 5 to add another secret named AWS_SECRET_ACCESS_KEY with AWS secret access key as shown in the below diagram:

> ![secret](https://github.com/Y2O-Dev/Github-Action-Workflow-CI/assets/114786664/4ee28256-8b50-42e7-ae52-9b89e00ee4d0)

## Step 2: Create a Dockerfile
- In the local repository, a Dockerfile was created  that defines how to build the Docker image. 

## Step 3: Create the GitHub Actions Workflow

- In the local repository as well, create a two nested folders in the root diectory named **_.github_** that will contain the **_workflows_** directory which will subsequently contains the _*image-push.yml*_ using the below command. 

>` mkdir -p .github/workflows && cd $_ && touch image-push.yml`

- The _*image-push.yml*_ file is the configuration file that defines the workflow for building and pushing a Node.js Docker image to Amazon ECR using GitHub Actions

## Step 4: Commit and Push Changes

- Commit all changes to the remote repository.

## Step 5: Verify the Workflow
- Once the changes are pushed to the master branch, GitHub Actions will automatically trigger the workflow defined in image-push.yml. 
- Prior to completing the changes to the files, `skip ci` was appended to the initial commit messages; this will prevent trigerring the workflows after pushing as shown in the below diagram:

>![skip_ci](https://github.com/Y2O-Dev/Github-Action-Workflow-CI/assets/114786664/386f1696-dd2f-4ea8-8455-92b9a50a00d0)

- The workflow will build the Docker image, tag it with the Git commit SHA , and push the image to the specified Amazon ECR repository as shown below.

>![image](https://github.com/Y2O-Dev/Github-Action-Workflow-CI/assets/114786664/9cfb11a7-c457-42e4-952f-7d411a8e967e)

- The various workflows steps completed successfully as printed below.

>![workflow](https://github.com/Y2O-Dev/Github-Action-Workflow-CI/assets/114786664/e6bf6307-533a-4b47-983b-edbd5459aa3d)

___
END