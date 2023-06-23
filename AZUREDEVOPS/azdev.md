# AZURE DevOps
* Azure DevOps is a pipeline tool. In this
    * Countinous Intigration
    * Countinous Delivery
    * Countinous Deployment
* Thats why it is also called as CI/CD pipelines.
## CI/CD Pipelines
#### Countinous Intigration:
* Continuous integration (CI) is the process of automatically building and testing code every time a team member commits code changes to version control. A code commit to the main or trunk branch of a shared repository triggers the automated build system to build, test, and validate the full branch.
#### Countinous Deployment:
* Continuous deployment (the other possible "CD") can refer to automatically releasing a developer’s changes from the repository to production, where it is usable by customers. It addresses the problem of overloading operations teams with manual processes that slow down app delivery.
![preview](./images/azdev1.png)
### Big Bang integration
* Consider a case where you are working for vintage systems where we are developing ecommerce application in Waterfall model.
* Application is in layered architecture
    * Presentation Layer
        * Web server
    * Business Layer
        * ECommerce server
    * Data Layer
        * image or video server
        * Data server
* Big Bang integrations are error prone, so best solution would be continuos integration (CI).
* The Goal of CI is to inform dev teams about the failures of integration.
* To perform CI different tools started like cruise control and hudson/jenkins
* Need for automated tests/unit tests started at this point.
##### Agile way of Software Development
* Agile had added smaller and frequent releases, this needs more aggressive automations than CI.
###### Expectation:
* Automated Pipeline which when developer pushes changes
    * Build/Package code
    * Code Quality and Security Issues
* Automate test executions with System, Performance, Reliablity, Security
* Report of the Quality of work done yesterday
* Customer and Internal Releases every 2 weeks
###### Plan ahead
    * Git Basics
    * YAML
    * Azure DevOPs
        * Boards
        * Build & Release Pipelines (*)
        * Artifacts
        * Documentation
        * Azure Source Repos
        * ****
##### Code Base: Open Source
    * .net
    * java
    * Workshop:
        * python
        * node js
#### Countinous Delivery:
* Continuous delivery (CD) is the process of automating build, test, configuration, and deployment from a build to a production environment. A release pipeline can create multiple testing or staging environments to automate infrastructure creation and deploy new builds.
* This pipeline will be triggered by the changes in the Version Control Systems (VCS).
#### WOW (Ways of Working)
* Figure out the manual steps
* Implement manual steps in Pipeline depending on your ci/cd engine
* Steps for gameoflife
* Softwares requried
    * git
    * jdk 8
    * maven
* Run the game of life manually by using following commands
---
* sudo apt update
* sudo apt install openjdk-8-jdk maven -y
* java -version
* mvn -version
* git clone https://github.com/wakaleo/game-of-life.git
* cd game-of-life
* mvn package
* cd gameoflife-web/target
* ls
---
* Pipeline in Jenkins
---
pipeline {
    agent any
    stages {
        stage ('vcs') {
            steps {
                git 'https://github.com/wakaleo/game-of-life.git'
            }
        }
        stage ('build') {
            steps {
                sh 'mvn package'
            }
        }
    }
}

---
* Pipeline in Azure DevOps
---
steps:
- task: Maven@4
  inputs:
    mavenPomFile: 'pom.xml'
    goals: 'package'
---
* Pipeline in git
---
run:
  script:
    - mvn package
    # run the command here
  artifacts:
    paths:
      - gameoflife-web/target/*.war

---
* Version control system is GIT
### Git
* Git is a Distributed Version Control System
* Git is Hosted by many providers
    * GitHub
    * Azure Source Repos
    * Code Commit
    * Bit Bucket
    * Git Lab


