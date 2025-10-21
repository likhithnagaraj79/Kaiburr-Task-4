# Task 4

# Table of Contents

* [Step 1: Start Jenkins](#step-1-start-jenkins)
    * [Navigate to Jenkins Directory](#step-1-start-jenkins)
    * [Start Jenkins Container](#start-jenkins-container-image)
    * [Check Jenkins Status](#check-if-jenkins-is-running)
    * [Access Jenkins](#access-jenkins-open-browser-and-go-to-httplocalhost8081jenkins)
* [Step 2: Get Jenkins Initial Password](#step-2-get-jenkins-initial-password)
* [Step 3: Complete Jenkins Setup Wizard](#step-3-complete-jenkins-setup-wizard)
    * [Install Suggested Plugins](#install-suggested-plugins)
    * [Create Admin User](#create-admin-user)
    * [Configure Jenkins URL](#jenkins-url)
* [Step 4: Configure Jenkins Tools](#step-4-configure-jenkins-tools)
    * [Configure Maven](#configure-maven)
    * [Configure JDK](#configure-jdk)
    * [Configure NodeJS](#configure-nodejs)
* [Step 5: Add Docker Hub Credentials](#step-5-add-docker-hub-credentials)
* [Step 6: Create Jenkins Pipeline for Backend (Task API)](#step-6-create-jenkins-pipeline-for-backend-task-api)

# Step 1: Start Jenkins

#Navigate to jenkins directory 
cd jenkins

![Navigate to jenkins](./Snapshots/1.1.png)

#Start Jenkins container Image  
docker-compose up -d

![Docker Compose](./Snapshots/1.2.png)

![Done Docker Compose](./Snapshots/1.3.png)

#Check if Jenkins is running 
docker ps

![Jenkins running](./Snapshots/1.4.png)

#Wait for Jenkins to start (30-60 seconds) 
#Check logs if needed
docker logs -f jenkins

![Jenkins started or not?](./Snapshots/1.5.png)

# Access Jenkins: Open browser and go to http://localhost:8081/jenkins 

![UI of Jenkins](./Snapshots/1.6.png)

# Step 2: Get Jenkins Initial Password 

![Password for Jenkins](./Snapshots/2.1.png)

# Step 3: Complete Jenkins Setup Wizard

    Install Plugins:

        Select "Install suggested plugins"

![Install plugins](./Snapshots/3.1.png)

        Wait for installation to complete

![Complete Installation](./Snapshots/3.2.png)


    Create Admin User: 

![Creating Admin User](./Snapshots/3.3.png)

        Username: admin (or your choice)
        Password: admin123 (or your choice)
        Full name: Your name
        Email: your email


    Jenkins URL:

        Keep default: http://localhost:8081/jenkins/ 

![Keep Default url](./Snapshots/3.4.png)

        Click "Save and Finish"

![Save and Finish](./Snapshots/3.5.png)

# Step 4: Configure Jenkins Tools

Configure Maven:

    Go to: Manage Jenkins → Global Tool Configuration

![Manage Jenkins](./Snapshots/4.1.png)

    Scroll to Maven section
    Click Add Maven

    Name: Maven-3.9.5
    Check "Install automatically"
    Version: 3.9.5,   

![Maven](./Snapshots/4.3.png)


Click Save

    Configure JDK:

    In same page, scroll to JDK section
    Click Add JDK

    Name: JDK-17
    Check "Install automatically"
    Add Installer: "Install from adoptium.net"
    Version: jdk-17.0.9+9


    Click Save

![JDK-17](./Snapshots/4.4.png)

Configure NodeJS:

    First install NodeJS plugin:

    Go to Manage Jenkins → Manage Plugins
    Click Available tab
    Search for "NodeJS"
    Install "NodeJS Plugin"
    Restart Jenkins when done

![NodeJS](./Snapshots/4.2.png)


    After restart, go to Manage Jenkins → Global Tool Configuration
    Scroll to NodeJS section
    Click Add NodeJS

    Name: NodeJS-18
    Check "Install automatically"
    Version: Select NodeJS 18.x (latest)


    Click Save

# Step 5: Add Docker Hub Credentials

Go to: Manage Jenkins → Manage Credentials
Click on (global) domain.

![Global Configuration](./Snapshots/5.1.png)

Click Add Credentials 

![Adding Credentials](./Snapshots/5.2.png)

Fill in:

Kind: Username with password
Scope: Global
Username: your-dockerhub-username (your Docker Hub username)
Password: your-dockerhub-password (your Docker Hub password)
ID: dockerhub-credentials
Description: Docker Hub Credentials


Click Create

![Credentials](./Snapshots/5.3.png)

![After Creating](./Snapshots/5.4.png)

# Step 6: Create Jenkins Pipeline for Backend (Task API)


From Jenkins Dashboard, click New Item 

![New Item](./Snapshots/6.1.png)

Enter name: task-api-pipeline 

![task-api-pipeline](./Snapshots/6.2.png)

Select: Pipeline
Click OK
In Configuration page:

Description: "CI/CD Pipeline for Task API"
Pipeline section:

Definition: Pipeline script 

![Pipeline Script](./Snapshots/6.3.png)

Click on Save

![After Clicking](./Snapshots/6.4.png)

Final Pipeline

![Pipeline](./Snapshots/6.5.png)
