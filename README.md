1.1. Create GIT Repository                                                                              //1    
2. Check the status of GIT Repository
3. Create user in GIT
4. List all users in GIT
5. Put files in repository to staging area
6. Commit the files which are added to staging area
7. Demonstrate git log command

steps
1. Create a Git Repository
Command:
git init
🔍 2. Check the Status of the Git Repository
Command:
git status
👤 3. Create a User in Git
Command:
git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"
📜 4. List All Users in Git
Command:
git config --list

📂 5. Put Files in Repository to Staging Area
Command:
git add filename


or to add all files:

git add .

🧱 6. Commit the Files Added to the Staging Area

Command:

git commit -m "Initial commit"
🕒 7. Demonstrate the git log Command

Command:

git log


2.1. Create GIT Repository                                                                             //2
2. Check the status of GIT Repository
3. Create user in GIT
4. List all users in GIT
5. Pull GIT remote repository(Github) to local repository
6. Create and switch to a new branch

🧭 1. Create a Git Repository

Command:

git init🔍
2. Check the Status of the Git Repository

Command:

git status
3. Create a User in Git

Command:

git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"
4. List All Users in Git

Command:

git config --list
🌐 5. Pull Remote Repository (GitHub) to Local Repository
Step 1: Clone the remote repository

Command:

git clone https://github.com/username/repository-name.git
Step 2: (If repo already initialized locally and you just want to pull updates)

Command:

git pull origin main
6. Create and Switch to a New Branch

Command (create + switch in one step):

git checkout -b feature-branch

3.1) Create GIT Repository                                                                              //3
2) Check the status of GIT Repository
3) Send GIT local repository to remote repository (Github)
4) Push local repository to remote repository

🧭 1️⃣ Create a Git Repository

Command:

git init
2️⃣ Check the Status of the Git Repository

Command:

git status
3️⃣ Send Local Repository to Remote Repository (GitHub)
Step 1: Create a New Repository on GitHub

Go to https://github.com

Click “New Repository”

Give it a name (e.g., myproject)

Don’t initialize with a README (you already have local files)

Copy the repository URL (it looks like this):

https://github.com/username/myproject.git

Step 2: Link Local Repository to Remote

Command:

git remote add origin https://github.com/username/myproject.git

4️⃣ Push Local Repository to Remote Repository
Step 1: Stage and Commit Files
git add .
git commit -m "Initial project setup"
tep 2: Push to GitHub

Command:

git push -u origin main

4.1. Create GIT Repository                                                                              //4
2. Pull GIT remote repository(Github) to local repository
3. Create and fork repository in GITHUB. Create and merge pull
request.

git init

git remote add origin <repository_URL>

git pull origin main

Go to GitHub → open repository → click Fork

Make changes in forked repository

Create a Pull Request from forked repo to original repo

Merge the Pull Request in the main repository


5.A. Create and build the job in Jenkins. B. Build a pipeline of jobs using maven                        //5
A. Create and build the job in Jenkins

Open Jenkins Dashboard.

Click “New Item”.

Enter job name → select “Freestyle project” → click OK.

In Source Code Management, choose Git → enter repository URL.

In Build Triggers, select Poll SCM or Build periodically (optional).

In Build Environment, select required options (e.g., clean workspace).

In Build section → choose Invoke top-level Maven targets.

Enter goal: clean install.

Click Save → then click Build Now.

B. Build a pipeline of jobs using Maven

Open Jenkins Dashboard → click New Item → select Pipeline → click OK.

In Pipeline script section, define pipeline script or use Pipeline script from SCM.

Example Jenkinsfile content:
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/username/repository.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }
}
Click Save → Build Now to run the pipeline

6.Create a maven project and show Junit4 and Jenkins integration                                        //6
with proper steps.
1. Create a Maven Project

Open Command Prompt / Terminal or use an IDE (like Eclipse or IntelliJ).

Run the following command to create a Maven project:

mvn archetype:generate -DgroupId=com.example \
-DartifactId=JenkinsJUnitDemo \
-DarchetypeArtifactId=maven-archetype-quickstart \
-DinteractiveMode=false


Move into your project folder:

cd JenkinsJUnitDemo

2. Add JUnit4 Dependency

Open the pom.xml file.

Add the following dependency inside <dependencies>:

<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.13.2</version>
    <scope>test</scope>
</dependency>


Save the file.

Run to verify dependencies:

mvn clean install

3. Create a JUnit4 Test

Inside src/test/java/com/example, create a file named AppTest.java.

Add the following code:

package com.example;

import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class AppTest {
    @Test
    public void testAddition() {
        int result = 2 + 3;
        assertEquals(5, result);
    }
}


Run tests:

mvn test

4. Install and Configure Jenkins

Open Jenkins Dashboard (http://localhost:8080
).

Click “New Item” → “Freestyle project” → OK.

Under Source Code Management, select Git → enter your repo URL.

Under Build, click Add Build Step → Invoke top-level Maven targets.

In Goals, enter:

clean test


Click Save and then Build Now.

5. Verify JUnit Results in Jenkins

After the build completes, go to the job page.

Click Build History → Console Output to see test execution logs.

To view reports visually:

Go to Manage Jenkins → Manage Plugins → Available

Install JUnit Plugin.

Re-run the build — you’ll now see Test Result Trend and JUnit reports in Jenkins.

7.Demonstrate how to:                                                                                     //7

1. Install the Role-Based Authorization Strategy plugin.
2. Create and configure the required roles.
3. Assign users to these roles.
4. Verify that each role has the correct permissions.
1. Install the Role-Based Authorization Strategy Plugin

Open Jenkins Dashboard → click Manage Jenkins.

Go to Manage Plugins → open the Available tab.

Search for “Role-based Authorization Strategy”.

Check the box → click Install without restart.

After installation, go back to Manage Jenkins → Configure Global Security.

Under Authorization, select “Role-Based Strategy” → click Save.

2. Create and Configure the Required Roles

Go to Manage Jenkins → Manage and Assign Roles → Manage Roles.

Under Global Roles, add roles such as:

admin

developer

viewer

Assign permissions:

admin → Select All permissions.

developer → Allow Job Create/Build/Read and Workspace.

viewer → Allow only Overall Read and Job Read.

Click Save.

3. Assign Users to These Roles

Go to Manage Jenkins → Manage and Assign Roles → Assign Roles.

Under Global roles, enter the username (e.g., alice, bob, charlie).

Assign:

alice → admin

bob → developer

charlie → viewer

Click Save.

4. Verify Each Role’s Permissions

Log out from Jenkins.

Login as each user:

alice (admin): Should see everything.

bob (developer): Should see projects and build them but cannot configure security.

charlie (viewer): Should only see project dashboards, not build or configure.

This confirms each role’s permissions are correctly applied.

8.Demonstrate how to:                                                                                    //8
1) Create a new Jenkins job (or use an existing one) and enable
remote build triggers. 2) Generate a unique authentication token for the job. 3) Demonstrate the correct syntax and parameters for a cURL
request that triggers the Jenkins build remotely.

1️⃣ Create a New Jenkins Job and Enable Remote Build Trigger

Open Jenkins Dashboard → click “New Item”.

Enter a job name → select “Freestyle project” → click OK.

Scroll to the Build Triggers section.

Check the option:
✅ “Trigger builds remotely (e.g., from scripts)”

In the Authentication Token field, enter a token (e.g., my-token).

Click Save.

2️⃣ Generate or View the Authentication Token

There are two ways to get the token:

A. Job-level token (simpler):

The token you set in Build Triggers (e.g., my-token) is used directly.

B. User API token (recommended for secure API calls):

Click your Jenkins username → Configure.

Scroll to API Token section.

Click Add new Token → name it (e.g., curl-trigger) → click Generate.

Copy the generated token — you’ll use it in the cURL command.

3️⃣ Use cURL to Trigger the Build Remotely
A. Without user API token (using build token only):
curl -X POST http://<JENKINS_URL>/job/<JOB_NAME>/build?token=<JOB_TOKEN>


Example:

curl -X POST http://localhost:8080/job/DemoJob/build?token=my-token

B. With user authentication (recommended):
curl -u <USERNAME>:<API_TOKEN> -X POST http://<JENKINS_URL>/job/<JOB_NAME>/build


Example:

curl -u admin:11a2b3c4d5e6f7g8h9i0j1k2l3 -X POST http://localhost:8080/job/DemoJob/build

C. To trigger a build with parameters (for parameterized jobs):
curl -u admin:<API_TOKEN> -X POST \
"http://localhost:8080/job/DemoJob/buildWithParameters?BRANCH=main&ENV=dev"

✅ Verification

Go to your Jenkins Dashboard → open the job.

You’ll see a new build appear in the Build History pane.

Click the build number → Console Output to confirm it was triggered remotely.

9.Demonstrate how to:                                                                                     // 9
1. Install the Role-Based Authorization Strategy plugin in Jenkins. 2. Create roles for Developer, QA Engineer, and Project Manager, each with
different levels of access
3. Assign specific users to the created roles based on their function
4. Restrict access for Project Manager to only viewing job status and build
history without any ability to modify jobs or trigger builds
5. Test the role assignments by logging in with different user accounts and
verifying that each user has access only to their respective action

1️⃣ Install Role-Based Authorization Strategy Plugin

Open Jenkins Dashboard → Manage Jenkins → Manage Plugins.

Click the Available tab and search for:
🔹 Role-based Authorization Strategy

Check the box → click Install without restart.

After installation, go to Manage Jenkins → Configure Global Security.

Under Authorization, select Role-Based Strategy.

Click Save.

2️⃣ Create Roles (Developer, QA Engineer, Project Manager)

Go to Manage Jenkins → Manage and Assign Roles → Manage Roles.

Under Global Roles, create:

developer

qa

project_manager

Assign permissions:

Role	Permissions
Developer	Job: Create, Configure, Build, Read
Overall: Read
QA Engineer	Job: Read, Build, Workspace
Overall: Read
Project Manager	Job: Read, Discover, ViewStatus
Overall: Read

Click Save.

3️⃣ Assign Users to Roles

Go to Manage Jenkins → Manage and Assign Roles → Assign Roles.

Under Global Roles, enter usernames and assign roles:

alice → developer

bob → qa

charlie → project_manager

Click Save.

4️⃣ Restrict Project Manager Access

For the Project Manager (charlie):

Allow only:

Overall → Read

Job → Read, Job → Discover, Job → ViewStatus

❌ Do not check permissions for Build, Configure, or Delete.

Click Save.

This ensures that Project Manager can only view build results and job status without changing or triggering anything.

5️⃣ Test Role Assignments

Log out of Jenkins.

Login as each user and verify permissions:

User	Role	What They Can Do
alice	Developer	Create, configure, and build jobs
bob	QA Engineer	View jobs, build them, and access workspace
charlie	Project Manager	Only view job status and build history (no modify/build options)

Attempt to perform restricted actions — Jenkins will show “Access Denied” for unauthorized tasks.

✅ Result:
Each user only has access according to their role:

Developers can develop and build.

QA Engineers can test builds.

Project Managers can monitor progress only.

10.To understand Continuous Integration.(exp 4)                                                           //10
1. Create a and build a freestyle project in jenkins by copying your git hub
repository url from your account. 2. Build this project and check this console output on jenkins.

1️⃣ Create and Build a Freestyle Project in Jenkins (Using GitHub Repo)
Step 1: Open Jenkins Dashboard

Go to your Jenkins URL → http://localhost:8080.

Log in with your Jenkins admin credentials.

Step 2: Create a New Freestyle Project

Click “New Item” on the Jenkins dashboard.

Enter a project name (e.g., CI-Demo-Project).

Select “Freestyle project” → click OK.

Step 3: Link GitHub Repository

In the project configuration page, scroll to Source Code Management.

Select Git.

In the Repository URL, paste your GitHub repo link, e.g.:

https://github.com/your-username/your-repo.git


If your repo is private:

Click Add Credentials → enter your GitHub username and Personal Access Token → Save.

Then select those credentials from the dropdown.

Step 4: (Optional) Add Build Triggers

To make this Continuous Integration:

Scroll to Build Triggers.

Check:
✅ Poll SCM (Jenkins checks GitHub periodically)
or
✅ GitHub hook trigger for GITScm polling (auto-builds on commits if webhook is configured).

Enter schedule (for Poll SCM), e.g.:

H/5 * * * *


→ Jenkins checks for updates every 5 minutes.

Step 5: Configure Build Step

Scroll to Build section.

Click Add build step → Execute shell (for Linux/macOS) or Execute Windows batch command (for Windows).

Enter simple build/test commands like:

echo "Starting Continuous Integration Build..."
mvn clean install
echo "Build completed successfully."

Step 6: Save and Build

Click Save.

On the project dashboard, click Build Now.

2️⃣ View Console Output

After the build starts, you’ll see a progress icon under Build History.

Click the Build Number (#1) → then click Console Output.

You’ll see logs like:

Started by user admin
Building in workspace /var/lib/jenkins/workspace/CI-Demo-Project
Cloning the remote Git repository
Fetching upstream changes from https://github.com/your-username/your-repo.git
Checking out Revision a1b2c3d4 (refs/remotes/origin/main)
[CI-Demo-Project] $ mvn clean install
...
BUILD SUCCESS
Finished: SUCCESS


✅ Result:

Jenkins cloned your GitHub project.

It automatically built it using Maven (or your build commands).

You verified the Console Output, confirming the Continuous Integration process works.

Configure Your Git User Information                                                                        //11
2) Clone the Repository
3) Open the file README.txt, make a minor change (e.g., add your name to the
contributors list), and save the file. 4) Check the Status of Your Repository
5) Stage the changes you made to README.txt for commit. 6) Commit Your Changes
7) Push Your Changes to the Remote Repository
8) Create and switch to a new branch called

1️⃣ Configure Your Git User Information
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"


✅ This sets your identity for all future Git commits.

2️⃣ Clone the Repository
git clone https://github.com/your-username/your-repository.git


✅ This downloads your GitHub repo into a local folder.

3️⃣ Edit README.txt

Open the file:

notepad README.txt   # (Windows)


or

nano README.txt      # (Linux/Mac)


Add your name under Contributors (e.g., Devyani Ayare).

Save and close the file.

4️⃣ Check the Status of Your Repository
git status


✅ It shows that README.txt has been modified (in red/untracked).

5️⃣ Stage the Changes
git add README.txt


✅ This moves the modified file to the staging area.

6️⃣ Commit Your Changes
git commit -m "Added my name to contributors list in README.txt"


✅ This permanently records the change in your local Git history.

7️⃣ Push Your Changes to the Remote Repository
git push origin main


✅ This uploads your commit to the GitHub repository’s main branch.

8️⃣ Create and Switch to a New Branch
git checkout -b feature-update


✅ This creates a new branch named feature-update and switches to it.

Summary Table:

Step	Command	Purpose
1	git config --global ...	Set user info
2	git clone	Copy remote repo locally
3	Edit file	Make change
4	git status	Check modified files
5	git add	Stage changes
6	git commit	Save change
7	git push	Upload to GitHub
8	git checkout -b	Create new branch
