# Step 1: Start Jenkins

#Navigate to jenkins directory Image 1.1
cd jenkins

#Start Jenkins container Image 1.2, 1.3, 
docker-compose up -d

#Check if Jenkins is running Image 1.4
docker ps

#Wait for Jenkins to start (30-60 seconds) Image 1.5
#Check logs if needed
docker logs -f jenkins

# Access Jenkins: Open browser and go to http://localhost:8081/jenkins , Image 1.6

# Step 2: Get Jenkins Initial Password Image 2.1

# Step 3: Complete Jenkins Setup Wizard

    Install Plugins:

        Select "Install suggested plugins", Image 3.1
        Wait for installation to complete, Image 3.2


    Create Admin User: Image 3.3

        Username: admin (or your choice)
        Password: admin123 (or your choice)
        Full name: Your name
        Email: your email


    Jenkins URL:

        Keep default: http://localhost:8081/jenkins/ Image 3.4
        Click "Save and Finish"

        Image 3.5

# Step 4: Configure Jenkins Tools

Configure Maven:

    Go to: Manage Jenkins → Global Tool Configuration, Image 4.1
    Scroll to Maven section
    Click Add Maven

    Name: Maven-3.9.5
    Check "Install automatically"
    Version: 3.9.5,   Image 4.3


Click Save

    Configure JDK:

    In same page, scroll to JDK section
    Click Add JDK

    Name: JDK-17
    Check "Install automatically"
    Add Installer: "Install from adoptium.net"
    Version: jdk-17.0.9+9


    Click Save, Image 4.4

Configure NodeJS:

    First install NodeJS plugin:

    Go to Manage Jenkins → Manage Plugins
    Click Available tab
    Search for "NodeJS"
    Install "NodeJS Plugin"
    Restart Jenkins when done,   Image 4.2


    After restart, go to Manage Jenkins → Global Tool Configuration
    Scroll to NodeJS section
    Click Add NodeJS

    Name: NodeJS-18
    Check "Install automatically"
    Version: Select NodeJS 18.x (latest)


    Click Save

# Step 5: Add Docker Hub Credentials

Go to: Manage Jenkins → Manage Credentials
Click on (global) domain.,  Image 5.1
Click Add Credentials ,     Image 5.2
Fill in:

Kind: Username with password
Scope: Global
Username: your-dockerhub-username (your Docker Hub username)
Password: your-dockerhub-password (your Docker Hub password)
ID: dockerhub-credentials
Description: Docker Hub Credentials


Click Create

Image 5.3

Image 5.4

# Step 6: Create Jenkins Pipeline for Backend (Task API)


From Jenkins Dashboard, click New Item ,  Image 6.1
Enter name: task-api-pipeline ,   Image 6.2
Select: Pipeline
Click OK
In Configuration page:

Description: "CI/CD Pipeline for Task API"
Pipeline section:

Definition: Pipeline script , Image 6.3

Image 6.4
