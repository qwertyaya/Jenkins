To create a Jenkins server with Jenkins Configuration as Code (CASC) and Docker Compose, you will need to have Docker and Docker Compose installed on your system. Then, you can follow these steps:

Create a directory for your Jenkins server and navigate to it in your terminal.

Create a file named docker-compose.yml and add the following content to it:

Copy code
version: '3'
services:
  jenkins:
    image: jenkins/jenkins:lts
    ports:
      - "8080:8080"
    volumes:
      - jenkins_home:/var/jenkins_home
    environment:
      CASC_JENKINS_CONFIG: /var/jenkins_home/jenkins.yaml
volumes:
  jenkins_home:

This configuration file will use the jenkins/jenkins:lts Docker image and map the Jenkins server's port 8080 to the host's port 8080. 
It will also create a volume for the Jenkins server's home directory, which will be used to store the Jenkins configuration file.

Create a file named jenkins.yaml in the same directory and add the following content to it:

jenkins:
  systemMessage: "Welcome to our Jenkins server"
  numExecutors: 2
  

This configuration file will set the system message that is displayed on the Jenkins dashboard and configure the number of executors (i.e., the number of concurrent builds that can be run) to 2.

Run the following command in your terminal to start the Jenkins server:

$ docker-compose up


Once the Jenkins server is up and running, you can access it in your web browser at http://localhost:8080.
To create a user, follow these steps:

On the Jenkins dashboard, click on the "Manage Jenkins" link in the left sidebar.

Click on the "Manage Users" link.

Click on the "Create User" button.

Enter the user's details (e.g., username, password, full name, and email address) and click on the "Create User" button.

The user will now be able to log in to the Jenkins server using the username and password you specified.
