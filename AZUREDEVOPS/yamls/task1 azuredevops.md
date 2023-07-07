### create self host agent, build and deploye the game of life
* To import the game of life code from git repositry. Then crate a token and self hosted agent. Build the pipeline by the following images.

![preview](./images/azdev11.png)
![preview](./images/azdev12.png)
![preview](./images/azdev13.png)
![preview](./images/azdev14.png)
![preview](./images/azdev15.png)

* Copy and save this token on notpad once it close then we regenrate only we did not get this token again.

![preview](./images/azdev16.png)

* Now select the token we get the options
    * Revoke == delete
    * Edit == If chages are there
    * Regenrate == to get the token

![preview](./images/azdev17.png)

* get the url of our organization this is also copy and save the notepad. We will use again.

![preview](./images/azdev18.png)
![preview](./images/azdev19.png)

* We create linux machine so we select the only this option only. copy and paste the download code on VM.

![preview](./images/azdev20.png)
![preview](./images/azdev21.png)
![preview](./images/azdev22.png)
![preview](./images/azdev23.png)
![preview](./images/azdev24.png)

* Here the url and token used.

![preview](./images/azdev25.png)
![preview](./images/azdev26.png)

```yaml
---
trigger:
  - main
pool:
  name: Default

parameters:
  - name: mavengoal
    displayName: Maven Goal
    type: string
    default: mavengoal
    values: 
      - package
      - Default
      - install
jobs:
  - job: buildgameoflifepackage
    displayName: Build game-of-life package
    steps:
      - task: Maven@3
        inputs:
          mavenPOMFile: 'pom.xml'
          goals: ${{ parameters.mavenGoal }}
          publishJUnitResults: true
          testResultsFiles: '**/surefire-reports/TEST-*.xml'
      - task: CopyPublishBuildArtifacts@1
        inputs:
          Contents: '**/target/gameoflife.war'
          ArtifactName: 'GameOfLifeArtifacts'
          ArtifactType: 'Container'
      - task: PublishBuildArtifacts@1
        inputs:
          PathtoPublish: '$(Build.ArtifactStagingDirectory)'
          ArtifactName: 'GameOfLifeArtifacts'
          publishLocation: 'Container'
```
![preview](./images/azdev27.png)
![preview](./images/azdev28.png)

### create microsoft host agent, build and deploye the game of life
* To  import the code and directly run the code on microsoft hosted agent by using the bellow yaml file.
* Build the pipeline by the following images.

![preview](./images/gol1.png)

![preview](./images/gol2.png)

![preview](./images/gol3.png)

![preview](./images/gol4.png)

![preview](./images/gol5.png)

![preview](./images/gol6.png)

![preview](./images/gol7.png)

![preview](./images/gol8.png)

![preview](./images/gol9.png)

![preview](./images/gol10.png)

![preview](./images/gol11.png)

* Yaml file for the gameoflife
```yaml
---
trigger:
  - main
pool:
  name: Azure Pipelines
  VmImage: ubuntu-20.04

parameters:
  - name: mavengoal
    displayName: Maven Goal
    type: string
    default: mavengoal
    values: 
      - package
      - Default
      - install
jobs:
  - job: buildgameoflifepackage
    displayName: Build game-of-life package
    steps:
      - task: Maven@3
        inputs:
          mavenPOMFile: 'pom.xml'
          goals: ${{ parameters.mavenGoal }}
          publishJUnitResults: true
          testResultsFiles: '**/surefire-reports/TEST-*.xml'
          javaHomeOption: 'JDKVersion'
          jdkVersionOption: '1.8'
      - task: CopyPublishBuildArtifacts@1
        inputs:
          Contents: '**/target/gameoflife.war'
          ArtifactName: 'GameOfLifeArtifacts'
          ArtifactType: 'Container'
      - task: PublishBuildArtifacts@1
        inputs:
          PathtoPublish: '$(Build.ArtifactStagingDirectory)'
          ArtifactName: 'GameOfLifeArtifacts'
          publishLocation: 'Container'
```

### create microsoft host agent, build and deploye the nopcommerce
* To  import the code and directly run the code on microsoft hosted agent by using the bellow yaml file.
* Build the pipeline by the following images.

![preview](./images/nop1.png)

![preview](./images/nop2.png)

![preview](./images/nop3.png)

```yaml
---
trigger:
  - master
pool:
  name: Azure Pipelines
  VmImage: ubuntu-20.04
variables:
  name: package
parameters:
  - name: dotnetgoal
    displayName: Dotnet Goal
    type: string
    default: dotnetgoal
    values: 
      - package
      - Default
      - install 

stages:
  - stage: buildnopcommerce
    displayName: Build nopCommerce
    jobs:
      - job: buildnopcommerce
        displayName: Build nopCommerce
        steps: 
          - task: DotNetCoreCLI@2
            inputs: 
              command: 'build'
              projects: src/NopCommerce.sln
          - task: DotNetCoreCLI@2
            inputs: 
              command: 'restore'
              projects: src/NopCommerce.sln
```


### create microsoft host agent, build and deploye the Spring Petclinic
* To  import the code and directly run the code on microsoft hosted agent by using the bellow yaml file.
* Build the pipeline by the following images.

![preview](./images/spc1.png)

![preview](./images/spc2.png)

![preview](./images/spc3.png)

```yaml
---
trigger:
  - main
pool: Default
variables: 
  - name: package
parameters: 
  - name: mavenGoal
    displayName: Maven goal
    type: string
jobs:
  - job: buildspringpetclinic
    displayName: Build spring-petclinic
    steps: 
      - task: Maven@3
        inputs:
          mavenPOMFile: 'pom.xml'
          goal: '${{ parameters.mavenGoal }}'
          publishJUnitResults: true
          testResultsFiles: '**/surefire-reports/TEST-*.xml'
          
      - task: CopyFiles@2
        inputs:
          Contents: '**/target/spring-petclinic*.jar'
          TargetFolder: $(Build.ArtifactStagingDirectory)
          - task: PublishBuildArtifacts@1
            inputs:
              PathtoPublish: '$(Build.ArtifactStagingDirectory)'
              ArtifactName: 'SpringPetclinicArtifacts'
              publishLocation: 'Container'
```
##### Concution:
* Done the build and deploy the 
  * gameoflife
  * nopcommerce
  * springpetclinic
  
