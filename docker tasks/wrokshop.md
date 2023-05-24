#### DAY1
# Run hello-world docker container and observe the container status
* Create a container by using following commands
---
  * docker container hello-world
  * docker container ls
  * docker info
---
![preview](./workshop1.png)
![preview](./workshop2.png)

### Check the docker images and write down the size of hello-world image
* To check the image size use the following command
---
  * docker image ls
---
![preview](./workshop3.png)

### Run the nginx container with name as nginx1 and expose it on 8080 port on docker host
* Create a container by using following commands
---
  * docker container run -d -p 8080:80 --name nginx1 nginx
---
![preview](./workshop4.png)
![preview](./workshop5.png)

### Explain docker container lifecycle
* Docker lifecycle has 6 states they are
  *  1.Create
  *  2.Run
  *  3.Stop
  *  4.Pause
  *  5.Unpause
  *  6.Delete
* Above states explained with example below commands
---
  * docker container run -d -p --name sravani nginx
  * docker container stop sravani
  * docker container start sravani
  * docker container pause sravani
  * docker container unpause sravani
  * docker container rm sravani
---
![preview](./workshop6.png)
![preview](./workshop7.png)

### Explain what happens when you run the docker container
* The docker run command creates running container by using docker images and can run commands inside them. When using the docker run command, a container can run a action.
* Show all the states of docker container on nginx based container
![preview](./workshop4.png)

### Explain the Docker architecture
* Docker architecture. Docker uses a client-server architecture. The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing your Docker containers. The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon.
![preview](./workshop8.png)

#### DAY2
### Write a Docker file for NodeJS application – expressjs
* Dockerfile
---
* FROM node:16-alpine
* RUN apk add --update
* RUN apk add git
* RUN git clone https://github.com/expressjs/express.git
* RUN cd express && \
      npm install express && \
      npm install -g express-generator@4 && \
      express /tmp/foo
* WORKDIR /tmp/foo
* RUN npm install
* EXPOSE 3000
* CMD ["npm", "start"]
---
* docker image build -t node:16-alpine .
* docker container run -d --name sravani -P node:16-alpine
---
![preview](./workshop9.png)
![preview](./workshop10.png)
![preview](./workshop11.png)

#### DAY3
### create a MySQL dB container from official MySQL image
* Select a image to run container from docker hub and run the container by using following commands.
---
* docker container run -d --name mysqldb -e MYSQL_ROOT_PASSWORD=srinivas -e MYSQL_DATABASE=employees -e MYSQL_USER=sravani -e MYSQL_PASSWORD=mutluri -P mysql:8
* docker container ls
---
![preview](./workshop12.png)

### login into SQL container and create a table
* To create a table we will enter inside the container and check the databases by using following commands
---
* docker container exec -it mysqldb mysql --password=srinivas
* show databases;
* use employees;
* CREATE TABLE employees ( PersonID int, LastName varchar(255), FirstName varchar(255), Address varchar(255), City varchar(255) );
* Insert into employees Values (1,'sravani','mutluri', 'ameerpet', 'hyd');
* Insert into employees Values (2,'srinivas','mutluri', 'mallavalli', 'nud');
* select * from employees;
---
![preview](./workshop13.png)
![preview](./workshop14.png)

## Try to create a persisted volume in MySQL container and mount that to other

---
docker container run -d --name sravani -v mysqldb:/var/lib/mysql -P -e MYSQL_ROOT_PASSWORD=rootroot -e MYSQL_DATABASE=students -e MYSQL-USER=sravani -e MYSQL_PASSWORD=rootroot mysql
* docker container run -d --name sravani --mount "source=sravani,target=/var/lib/mysql,type=volume" -P -e MYSQL_ROOT_PASSWORD=rootroot -e MYSQL_DATABASE=students -e MYSQL-USER=sravani -e MYSQL_PASSWORD=rootroot mysql
---
![preview](./workshop15.png)
![preview](./workshop16.png)

#### DAY4
### Create an alpine container in interactive mode and install python
* Manual step
* Create a container by using following commands
* ---
* <docker container run -it --name sravani alpine:latest>
* <apk --update upgrade>
* apk add python3
* <python3 --version>
* ---
* ![Preview](./workshop17.png)
* ![Preview](./workshop18.png)
* By using Dockerfile and create container
* ---
* FROM alpine:latest
  LABEL author="sravani" organization="techinfo" project="python"
  RUN apk --update upgrade
  RUN apk add python3
  CMD ["python3 --version"]
* ---
* Now build the image by using following command
* ---
* <docker image build -t python .>
* <docker image ls>
* ---
* ![Preview](./workshop19.png)
* ![Preview](./workshop20.png)

### Create a ubuntu container with sleep 1d and then login using exec and install python
* login to docker playground in terminal and create container by using following commands.
* ---
* docker container run -d --name py -P ubuntu:20.04 sleep 1d
* docker container exec -it py /bin/bash
* apt update
* apt install python3 -y
* python3 --version
* ---
* ![Preview](./workshop21.png)
* ![Preview](./workshop22.png)
* ![Preview](./workshop23.png)
* ![Preview](./workshop24.png)

### Create a postgres container with username panoramic and password as trekking. Try logging in and show the databases (query for psql)
* login to docker playground in terminal and create postgres by using following commands
* ---
* docker container run -d --name database -e POSTGRES_USER=panoramic -e POSTGRES_PASSWORD=trekking -e POSTGRES_DB=psqldata -P postgres:15
* docker container exec -it database postgres --password=trekking
* docker exec -it database /bin/bash
* psql --help
* ---
* ![Preview](./workshop25.png)
* ![Preview](./workshop26.png)
* To create table 
* ---
* psql -U panoramic -W trekking -d psqldata
* CREATE TABLE Persons (
    PersonID int,
    LastName varchar(295),
    FirstName varchar(295),
    Address varchar(295),
    City varchar(295)
);
* Insert into Persons Values (1, 'sravani', 'mutluri', 'ameerpet', 'hyd');
* Insert into Persons Values (2, 'srinivas', 'mutluri', 'ameerpet', 'hyd'); 
* SELECT * from Persons;
* ---
* ![Preview](./workshop27.png)
* ![Preview](./workshop28.png)

### Try to create a docker file which runs php info page, use ARG and ENV wherever appropriate on
# apache server
* login to docker playground in terminal and create a dockerfile for apache server
* ---
* FROM ubuntu:22.04
  LABEL author="sravani" organization="QT tech" project="apache"
  ARG DEBIAN_FRONTEND=noninteractive
  RUN apt update && apt install apache2 -y
  RUN apt install php libapache2-mod-php -y
  RUN echo "<?php phpinfo() ?>" >> /var/www/html/info.php
  EXPOSE 80
  CMD ["apache2ctl","-D","FOREGROUND"] 
* ---
* After creating dockerfile to build the image use the following commands.
* ---
* docker image build -t apache .
* docker container run --name php -d -P apache
* docker container ls
* ---
* ![preview](./workshop29.png)
* ![preview](./workshop30.png)
* Now we observe the port number and open that port.
* ![Preview](./workshop31.png)

# nginx server
* login to docker playground in terminal and create a dockerfile for nginx server
* ---
* FROM ubuntu:22.04
  LABEL author="sravani" organization="techinfo" project="nginx"
  ARG DEBIAN_FRONTEND=noninteractive
  RUN apt update && apt upgrade -y
  RUN apt install nginx -y
  RUN apt install php php-fpm -y
  RUN rm -rf /var/lib/apt/lists/
  COPY nginx.conf /etc/nginx/sites-available/default
  RUN chmod -R 777 /var/www/html
  RUN echo "<?php phpinfo() ?>" >> /var/www/html/info.php
  EXPOSE 80
  ENTRYPOINT ["/bin/bash","-c","service php-fpm start && nginx -g 'daemon off;'"]
  CMD ["nginx","-g","daemon off;"]
* ```
* After creating dockerfile to build the image use the following commands.
* ---
* docker image build -t nginx .
* docker container run --name php -d -P nginx
* docker container ls
* ---
* ![Preview](./workshop32.png)
* ![Preview](./workshop33.png)

### Create a Jenkins image by creating an own docker file
* login to docker playground in terminal and create a dockerfile for jenkins server
* ---
* FROM ubuntu:22.04
  LABEL author="sravani" organization="techinfo" project="jenkins"
  RUN apt update && apt install openjdk-11-jdk maven curl -y
  RUN curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | tee \
      /usr/share/keyrings/jenkins-keyring.asc > /dev/null
  RUN echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
      https://pkg.jenkins.io/debian-stable binary/ | tee \
      /etc/apt/sources.list.d/jenkins.list > /dev/null
  RUN apt-get update 
  RUN apt-get install jenkins -y
  EXPOSE 8080
  CMD ["/usr/bin/jenkins"]
* ---
* After creating dockerfile to build the image use the following commands.
* ---
* docker image build -t sravani .
* docker container run -d --name sravani -P jenkins/jenkins
* ---
* ![Preview](./workshop34.png)
* ![Preview](./workshop35.png) 

### Create nop commerce and MySQL server and try to make them work by configuring
# nop commerce
* 
---
* FROM mcr.microsoft.com/dotnet/sdk:7.0
  LABEL author="sravani" organization="techinfo" project="nopcommerce"
  ADD https://github.com/nopSolutions/nopCommerce/releases/download/release-4.60.2/nopCommerce_4.60.            2_NoSource_linux_x64.zip /nop/nopCommerce_4.60.2_NoSource_linux_x64.zip
  WORKDIR /nop
  RUN apt update && apt install unzip -y && \
      unzip /nop/nopCommerce_4.60.2_NoSource_linux_x64.zip && \
      mkdir /nop/bin && mkdir /nop/logs
  EXPOSE 5000
  ENV ASPNETCORE_URLS="http://0.0.0.0.0:5000"
  CMD [ "dotnet", "Nop.Web.dll" ]
---
* After creating dockerfile to build the image use the following commands.
---
* docker image build -t nop .
* docker network create -d bridge --subnet "10.0.0.0/24" mysqlnetwork
* docker volume create mysqlvolume
* docker container run --name mynop1 -d -P --network mysqlnetwork -e MYSQL_SERVER=mysqldb nop
* docker container run -d --name hema -e MYSQL_ROOT_PASSWORD=srinivas -e MYSQL_DATABASE=test -e MYSQL_USER=sravani -e MYSQL_PASSWORD=mutluri --network mysqlnetwork -v mysql:/var/lib/mysql mysql:5.6
* docker container ls
---
* ![Preview](./workshop36.png) 
* ![Preview](./workshop37.png) 
* ![Preview](./workshop38.png)
* ![Preview](./workshop39.png)
* ![Preview](./workshop40.png)
* ![Preview](./workshop41.png)

#### DAY 5
### Multi stage Docker file and push images to azure/aws registries and docker compose file for following applications
## nopCommerce


## stage-1
  FROM ubuntu:22.04 as nopCommerce
  RUN apt update && apt install unzip -y
  ARG DOWNLOAD_URL=https://github.com/nopSolutions/nopCommerce/releases/download/release-4.60.2/nopCommerce_4.60.2_NoSource_linux_x64.zip
  ADD ${DOWNLOAD_URL} /nopCommerce/nopCommerce_4.60.2_NoSource_linux_x64.zip
  RUN cd /nopCommerce && unzip nopCommerce_4.60.2_NoSource_linux_x64.zip && \
  mkdir bin logs && rm nopCommerce_4.60.2_NoSource_linux_x64.zip
## stage-2
  FROM mcr.microsoft.com/dotnet/sdk:7.0
  LABEL author="manu" organization="khaja.tech" project="nop"
  ARG DIRECTORY=/nop
  WORKDIR ${DIRECTORY}
  COPY --from=nopCommerce  /nopCommerce ${DIRECTORY}
  EXPOSE 5000
  ENV ASNETCORE_URLS="http://0.0.0.0:5000"
  CMD ["dotnet","Nop.Web.dll","--urls","http://0.0.0.0:5000"] 
  














FROM alpine/git AS vcs
RUN git clone https://github.com/spring-projects/spring-petclinic.git && \
    pwd && ls /git/spring-petclinc


FROM maven:3-amazoncorretto-17 AS builder
COPY --from=vcs /git /spring-petclinic
RUN ls /spring-petclinic
RUN cd spring-petclinic
RUN mvn package


FROM amazoncorretto:17-alpine-jdk
LABEL author="sravani"
EXPOSE 8080
ARG HOME_DIR=/spc
WORKDIR ${HOME_DIR}
COPY --from=builder /spring-petclinic/target/spring-*.jar ${HOME_DIR}/spring-petclinic.jar
EXPOSE 8080
CMD ["java", "-jar", "spring-petclinic.jar"]