# Install and Configure Jenkins

## Prerequisite
The following instruction requires GCP Compute Instance, see article: https://medium.com/@shiv.jalli_26300/gcp-create-a-compute-instance-5343ac3ac443

# Installation
In the browser, cloud console, navigate to Compute Engine, VM Instances. Click on the SSH button to open an ssh terminal.

## Install Java 8
Enter the following commands in the ssh terminal
```
java -version
sudo apt-get update
sudo apt install openjdk-8-jdk
java -version
```
## Set up to Install Jenkins
To install the latest version of Jenkins, add the repository key to the system, and add the repository address to the sources list.
```
wget -q -O \
  - https://pkg.jenkins.io/debian-stable/jenkins.io.key \
  | sudo apt-key add -
```
```
sudo sh -c \
  'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
  /etc/apt/sources.list.d/jenkins.list'
```
## Install Jenkins
```
sudo apt-get update
sudo apt-get install jenkins
```
## Check Jenkins is running
```
systemctl status jenkins
```
>● jenkins.service — LSB: Start Jenkins at boot time <br />
Loaded: loaded (/etc/init.d/jenkins; generated) <br />
Active: active (exited) since Fri 2020–08–14 15:14:21 UTC; 1min 19s ago <br />

# Get Information to Invoke Jenkins

Get the initialAdminPassword
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
## Open Jenkins in Browser
```
http://<external IP address of Virtual Machine>:8080/
```

## Enter the initialAdminPassword
```Enter new username, password details
Install suggested plugins
👏 Welcome to Jenkins!
```

# Create the First Job
From the browser Dashboard (initial) Jenkins page, click

```
New Item
```

## Enter an item name
```
First Job
```

## Click Build Environment and check
```
✅ Delete workspace before build starts
✅ Add timestamps to the Console Output
```
Click Build, Click “add build step” and then select “Execute shell”

Enter a shell command and click Save

```
echo "This is my first job"
```

## Build it
From the browser Project First Job page, click

```
Build Now
```

## Examine the Job
Under the Build History Click the job number <b>#1</b>, and select console output

# Stop and Start Jenkins
```
systemctl stop jenkins
systemctl start jenkins
```
---

# Install Plugins

## Verify Git
In the browser cloud console, navigate to Compute Engine, VM Instances. Click on the SSH button to open an ssh terminal.
```
git --version
```

If required Install Git
```
sudo apt-get install git
```

## Install Github Plugin
From the browser Dashboard Jenkins page, click
```
Manage Jenkins
```
Click Manage Plugins and then select the available Tab

```
Type "Github", check Github Integration and then click Install without restart
✅ GitHub Integration
👏 Githun plugin installed.
```

## Install Maven

In the browser cloud console, navigate to Compute Engine, VM Instances. Click on the SSH button to open an ssh terminal.

## Verify Maven

```
mvn --version
```

If required Install Maven

```
sudo apt-get update
sudo apt-get install maven
mvn --version
```
>Apache Maven 3.6.0 <br />
>Maven home: /usr/share/maven<br />

## Configure Jenkins

From the browser Dashboard Jenkins page, click Manage Jenkins and then click Global Tool Configurations

Set Java and Maven
```
Name: Java8
JAVA_HOME: /usr/lib/jvm/java-8-openjdk-amd64
```
```
Name: DefaultMaven
MAVEN_HOME: /usr/share/maven
👏 Click Save ~ Basic Configuration completed
```
