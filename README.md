[![View in Stacksmith](https://img.shields.io/badge/view_in-stacksmith-00437B.svg)](https://stacksmith.bitnami.com/p/bitnami-public/apps/5cc27550-b504-0136-77eb-52659d017641)

# Jenkins

This is a simple guide to show how to deploy Jenkins using [Bitnami Stacksmith](https://stacksmith.bitnami.com)

## Package and deploy with Stacksmith

1. Go to [stacksmith.bitnami.com](https://stacksmith.bitnami.com).
2. Create a new application and select the `Java Tomcat Application` stack template.
3. Select the targets you are interested on (AWS, Kubernetes,...).
4. Find and download your desired Jenkins version at https://jenkins.io/download/. You can download the latest version directly from http://mirrors.jenkins.io/war-stable/latest/jenkins.war, or by running the command below:

   ```bash
   wget http://mirrors.jenkins.io/war-stable/latest/jenkins.war
   ```

5. Upload the `jenkins.war` application file to Stacksmith. Note that you can provide any version of Jenkins.
6. Select `Git repository` for the application scripts and paste the URL of this repo. Use `master` as the `Repository Reference`.
7. Click the <kbd>Create</kbd> button.
8. Wait for app to be built and deploy it in your favorite target platform.

Stacksmith will compare the latest commit for a reference (e.g. new commits made to a branch) against the last commit used during packaging. If there are any new commits available, these will be available to view within the `Repository Details` pane in the application history. If you choose to repackage your application, these newer commits will be incorporated and used during the packaging.

### Update the application with Stacksmith

1. Download a new version of Jenkins. You can download the latest available version at http://mirrors.jenkins.io/war-stable/latest/jenkins.war, or with the command below:

   ```bash
   wget http://mirrors.jenkins.io/war-stable/latest/jenkins.war
   ```

2. Go to your app [stacksmith.bitnami.com](https://stacksmith.bitnami.com)
3. Click on <kbd>Edit configuration</kbd>, delete the existing `jenkins.war` and upload the new `jenkins.war` file.
4. Click <kbd>Update</kbd>.
5. Wait for the new version to be built and re-deploy it in your favorite target platform.

Stacksmith will use the latest Application Scripts from the GitHub repository.

## Use the Stacksmith CLI for automating the process

1. Go to [stacksmith.bitnami.com](https://stacksmith.bitnami.com), create a new application and select the `Java Tomcat Application` stack template.
2. Install [Stacksmith CLI](https://github.com/bitnami/stacksmith-cli) and authenticate with Stacksmith.
3. Download the latest version of Jenkins at http://mirrors.jenkins.io/war-stable/latest/jenkins.war, or with the command below:

   ```bash
   wget http://mirrors.jenkins.io/war-stable/latest/jenkins.war
   ```

4. Edit the `Stackerfile.yml`,  update the `appId` with the URL of your project and the name of `userUploads`.
5. Run the build for a specific target like `aws` or `docker`. E.g.

   ```bash
   stacksmith build --target docker
   ```
6. Wait for app to be built and deploy it in your favorite target platform.

### Update the application via CLI

1. Download the latest version of Jenkins at http://mirrors.jenkins.io/war-stable/latest/jenkins.war, or with the command below:

   ```bash
   wget http://mirrors.jenkins.io/war-stable/latest/jenkins.war
   ```

2. Run the build for a specific target like `aws` or `docker`. E.g.

   ```bash
   stacksmith build --target docker
   ```

3. Wait for the new version to be built and re-deploy it in your favorite target platform.

## Scripts

In the `stacksmith/user-scripts` folder, you can find the required scripts to build and run this application:

### build.sh

This script takes care of installing the application and its dependencies. It performs the next steps:

* Adds the system user that will run the application.
* Uncompress the application code to the `/opt/app` folder.
* Adjust the application files permissions.
* Install dependencies.

### boot.sh

This script takes care of configuring the application.
