# Simple-webapp

This project is a simple web application built using HTML, Docker, and Jenkins. It demonstrates a basic CI/CD pipeline that builds and deploys the web app using Jenkins.

### Prerequisites
Before you start, ensure that you have the following installed on your system:

Docker
Jenkins

### Getting Started

1. Clone the project repository using git clone <https://github.com/Supu-27/Simple-webapp.git>.
2. Navigate to the project directory using cd <Simple-webapp>.
3. Build the Docker image using the following command:

```
docker build -t my-web-app .
```

4. Start the Docker container using the following command:

```
docker run -d --name my-web-app -p 80:80 my-web-app
```

5. Open a web browser and go to http://localhost to view the web app.

![Webapp](![image](https://user-images.githubusercontent.com/125067454/236525689-4dd87aca-e72a-4de9-bb68-9c0ac290e4ab.png)
![Snap](![image](https://user-images.githubusercontent.com/125067454/236526139-bd47db5c-a976-4786-a7ab-5b525e45ec91.png)



### Jenkins Automation

This project can be automated using Jenkins master-slave architecture with webhook. Here are the steps to set it up:

### Step 1: Set up Jenkins Master-Slave Architecture

Install Jenkins on the master node.
Set up a slave node with Docker installed.
Add the slave node to Jenkins and configure it.

### Step 2: Set up the Jenkins Pipeline

Create a new Pipeline job in Jenkins.
Set the Pipeline script to the following:

```
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t my-web-app .'
            }
        }
        stage('Deploy') {
            steps {
            sh 'docker run -d --name my-web-app -p 80:80 my-web-app'
            }
        }
    }
}

```
![Pipeline-Snap](![image](https://user-images.githubusercontent.com/125067454/236525412-bbf6c2b2-281c-4a9a-b3ad-39b60a306f96.png)


### Step 3: Add a Webhook

1. In your GitHub repository, go to Settings > Webhooks > Add webhook.
2. Set the Payload URL to http://34.204.91.112:8080/github-webhook/.
3. Set the Content type to application/json.
4. Select the events you want to trigger the webhook.
5. Click Add webhook.

Now, every time you push changes to your repository, Jenkins will automatically build and deploy the updated application.

### Conclusion

This project demonstrates a basic CI/CD pipeline using Jenkins, Docker, and Git. With the addition of a webhook, you can automate the build and deployment process even further.
