---
title: "How to integrate Sonarqube to Jenkins"
seoTitle: "A Jenkins pipeline with sonarqube"
datePublished: Wed Dec 20 2023 07:39:57 GMT+0000 (Coordinated Universal Time)
cuid: clqdgrco3000z08js7fmfhlci
slug: jenkins-sonarqube
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703057775784/41a6c2f4-0cb5-4332-ae8e-af38dfa2dfa8.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1703057944082/57554fe6-d5eb-47a1-8e50-11970a1a5e55.png
tags: docker, sonarqube, devops, jenkins, configuration, ci-cd, sonarqube-installation

---

### **Welcome, fellow developers!**

Are you tired of manually analyzing your code quality? Do you want to seamlessly automate and integrate the process into your CI/CD pipeline? Well, then you've come to the right place!

Today's blog post is all about integrating SonarQube with Jenkins, two powerful tools that can help you improve your software quality and development process.

So, buckle up and get ready to learn how to:

* **Install and configure SonarQube and Jenkins**
    
* **Set up a SonarQube Scanner in Jenkins**
    
* **Run Jenkins Pipeline**
    

By the end of this blog post, you'll be able to confidently integrate SonarQube and Jenkins to ensure the quality of your software throughout the development lifecycle. Let's dive in!

## Install and Configure SonarQube and Jenkins

We will be using Docker to install SonarQube and Jenkins. So make sure that you have installed Docker in your system.

### Jenkins

First, we will install Jenkins. To download and run the Jenkins docker image we will use this command.

```basic
docker run -d -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11
```

After running this code the docker will download the docker image from the docker hub and then run it on port 8080. We have also created a volume so that we can store the data so that if the docker container gets crushed and restarted again it can get all the reviews configuration.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702900627075/410027a7-ea38-456b-837d-9af1277ce61d.png align="center")

You can use the command `docker ps` to see the running container. if it is running open your browser then visit `localhost:8080` it will ask you to create a username and password and then install some plugin.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702902580893/abd9764f-a3cb-4e64-84d5-c4492656c876.png align="center")

### SonarQube

To install sonarQube we will use docker compose because we have sonarQube needs a database to store all the data on that database. To do so we will docker-compose file.

```dockerfile
  version: "3"

  services:
    sonarqube:
      image: sonarqube:lts-community
      depends_on:
        - db
      environment:
        SONAR_JDBC_URL: jdbc:postgresql://db:5432/sonar
        SONAR_JDBC_USERNAME: sonar
        SONAR_JDBC_PASSWORD: sonar
        SONAR_ES_BOOTSTRAP_CHECKS_DISABLE: "true"
      volumes:
        - sonarqube_data:/opt/sonarqube/data
        - sonarqube_extensions:/opt/sonarqube/extensions
        - sonarqube_logs:/opt/sonarqube/logs
      ports:
        - "9000:9000"
    db:
      image: postgres:12
      environment:
        POSTGRES_USER: sonar
        POSTGRES_PASSWORD: sonar
      volumes:
        - postgresql:/var/lib/postgresql
        - postgresql_data:/var/lib/postgresql/data

  volumes:
    sonarqube_data:
    sonarqube_extensions:
    sonarqube_logs:
    postgresql:
    postgresql_data:
```

This docker file will pull the sonarqube image with some env, volume, and posts and then we have the Postgres database image.

To run this `docker compose.yaml` the file we have to use the command `docker compose -f "Docker Compose.yml" up -d --build`.

When it is built and starts you can go to `localhost:9000`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702902596481/a7fab650-9c9b-48b4-968c-dd3d9e70b48d.png align="center")

## **Set up a SonarQube Scanner in Jenkins**

### First, we will step up our Jenkins

1 - Login with your username and password that you have created while logging in on Jenkins.

2 - Created a pipeline by clicking on `New item` then write the project name select pipeline and press OK.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702903111302/3e7ad5cc-87ae-446b-8f10-cc2a6df1075f.png align="center")

3 - Now you have to put all the necessary details to configure the Jenkins project.

A. **GitHub project** - with your GitHub project link

B. **GitHub hook trigger for GITScm polling**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702903428344/7f2d3317-2688-4a9f-81ba-9968d1d01d90.png align="center")

C. Pipeline Configuration

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702903412541/de0d6c1b-1aed-4219-a502-4366a541bf6b.png align="center")

Now the Save it.

Now we will install Sonarqube plugins. to do that we will first go to `manage jenkins`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702910517040/da4047c6-ab3d-445e-bb4d-0e28742ddb72.png align="center")

Then click `Plugins` -&gt; `Available plugins` (in my case I have already installed Sonarqube)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702911128625/34d7a8f2-a5a9-4474-a5e4-a9f039b849fd.png align="center")

Now back to `manage Jenkins` --&gt; `Tools` and find **SonarQube Scanner installations.** Once you have found the Click on `Add SonarQube Scanner`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702911748871/76346ae8-d5b1-45d3-a914-8dd27b33c05a.png align="center")

You have to fill it up in the same way. As I have shown you here.

Now we have added the sonarqube server. To do that go to the `manage Jenkins` --&gt; `System` and fine **SonarQube servers.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703008730734/90f640bd-d4ee-4949-a5f2-0bd567f25fd2.png align="center")

> your url of the `sonarQube-server` is `localhost:9000` but it can not access that so we have to give it a prober url. So we will give our machine url.

Give the sonarQube Servers Name `sonar-server` and server URL

### Now, we will step up our SonarQube

After login to the SonarQube Dashboard, we will create a new project and give the project name.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702997957842/b816171e-163b-42b6-8926-ffd7362f552b.png align="center")

After selecting Jenkins

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702998027492/f5904543-9628-4873-9315-01e1e36fd095.png align="center")

Now select GitHub if you have your code in GitHub.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702998047169/9ef55bd5-4a65-4fa1-9554-377f8265dfaa.png align="center")

1 - After selecting it will ask you to configure Jenkins first we have to create the Jenkins pipeline which we all already have done. So click on continue.

2 - The next step is to **Create a GitHub Webhook** To do that we go to the GitHub repo of your project and then click on the **setting**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702998902363/18d60995-e56e-43fc-85a9-c38394ea6abc.png align="center")

Then Click on **Webhooks** and then click on **Add Webhooks.**

> In the url section you have to give the url of jenkins but the proble it that we are using docker to run jenkins which is avable on your machine which me github can't access you jenkins. To do that we have to forward that your are to a public url so that github can access the jenkins.

So we will use [https://ngrok.com/docs/getting-started/](https://ngrok.com/docs/getting-started/) to forward the `localhost:8080` which is for jankins. After installing ngrok use this command to created a new URL.

```dockerfile
ngrok http 8080
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703002330433/15fc2ef9-66f9-43b3-bc42-448a5bec75b4.png align="center")

Now copy that URL and past on the GitHub webhooks page after the URL you have to write `/github-webhook/`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703002794126/bb3bb700-e91c-43c3-8844-d56b2a1dfdd5.png align="center")

Make sure your URL should look like this.

3 - Now create a file with the name `sonar-project.propertie` and past this code on that file.

```yaml
sonar.projectKey=netflixs
```

Now Create a Jenkinsfile in your repo with the name `jenkinsfile` and past this code on that.

```yaml
node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}
```

Now it is done. All the configuration is done.

## **Run Jenkins Pipeline**

Now push all the code and files that push created into your GitHub repo.  
Now every is right the moment you push the code the Jenkins pipeline will trigger and start doing the job that is given to it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703004697225/cbd5d4a9-57f4-4bf0-85c7-909cac77a7d8.png align="center")

As you can see I have also failed so many times so you also have to keep trying until you pipeline runners successfully.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703007514749/6520f0f2-da57-4ca8-948f-1f66cce3b8ee.png align="center")

# THE END

Thank You for reading this blog it you have any doubt or you stuck on a problem please let me I will be very much happy to help you.