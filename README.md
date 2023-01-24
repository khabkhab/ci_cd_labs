# Goal: Dockerize a Java Web Application using docker-compose

Created solution is for the lab: [dockerize](https://www.devopsrealtime.com/dockerize-a-java-web-application-using-docker-compose/)

Short description:

Start an app based on Tomcat that uses Nginx and SQL for the web and database parts, respectively.

## Solution:
1. Dockerfile

    1.1. Usage of maven: 3.8-openjdk-18-slim image to clone the git repo, move source files, and build an app

    1.2. Next application of amazonlinux image and installation of java, telent, and mysql.

    1.3. Build image

2. Docker-compose:

    2.1. Creates 3 containers for nginx, tomcat, mysql

    2.2. NGINX: add volume with nginx.conf file.

    2.3. TOMCAT: add two volumes to bind tomcat-user.xml and application properties.

    2.4. MySQL: add volume to bind database file dump.sql

    2.5. Separate networks. Frontend: NGINX + TOMCAT; Backend: TOMCAT + MySQL



#### Note: Java is looking for .jar files. If non found it will terminate the process. To avoid it the line: 

### "tomcat.util.scan.StandardJarScanFilter.jarsToSkip=*.jar" 

#### was added to application.properties


#### Additionally, my sincere gratitude to Alexandr for his help, patiente and explanation. Check his [github](https://github.com/just4lex) account.