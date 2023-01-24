# create the image
    # create all that is needed to build the app 

        #usage of the maven
FROM maven:3.8-openjdk-18-slim as build
        #collects an app from the github
RUN apt update && apt-get install -y git && \
        git clone https://bitbucket.org/dptrealtime/java-login-app.git /usr/src/app
        #put the app together
RUN cd /usr/src/app/ && mvn package
        #usage of amazonlinux
FROM amazonlinux:2.0.20221210.0
        #installation of java, telnet, mysql
RUN amazon-linux-extras install epel -y && \
    yum install -y https://dev.mysql.com/get/mysql80-community-release-el7-5.noarch.rpm && \
    yum install -y mysql-community-server && \
    yum install -y java telnet

        #copy dptweb-1.0.war file 
COPY --from=build /usr/src/app/target/dptweb-1.0.war /dptweb-1.0.war 
        #exposing the port
EXPOSE 8080
        #runs the app once the container initiated
CMD [ "java",  "-jar", "/dptweb-1.0.war" ]