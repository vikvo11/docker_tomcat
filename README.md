# docker_tomcat
1

It turns out that all default tomcat apps have been removed from the webapps directory for all tomcat images starting with Tomcat version 7. All apps have been moved to /usr/local/tomcat/webapps.dist directory so that they are not launched by default. You can read about it here.

If you still want to access those default apps you can copy them back to the webapps directory, if you wish:

FROM tomcat:9.0
RUN mv /usr/local/tomcat/webapps.dist/* /usr/local/tomcat/webapps/
CMD ["catalina.sh","run"]
or copy only the apps that you want. Also you will have to edit tomcat configuration files to not get 403 when accessing those apps.

####
version: '3'
  2 services:
  3   prod:
  4     container_name: tom
  5     command: /bin/bash
  6     build: ./tomcat
  7     volumes:
  8       - ./tomcat:/usr/src/app
  9     ports:
 10       - 8888:8080

docker-compose run prod
###
docker-compose up
docker-compose exec prod sh

https://medium.com/@durganath/how-to-deploy-java-application-using-tomcat-in-docker-aws-8ac5eb5b8226

### build

https://husbch.medium.com/mini-project-deploying-java-application-with-tomcat-bd7d96bfcc7

mkdir -p src/main/java/hello

docker run -it --rm --name my-maven-project -v "$(pwd)":/usr/src/mymaven -w /usr/src/mymaven maven:3.3-jdk-8 mvn clean install


cp docker_maven/target/gs-maven-0.1.0.war docker_tomcat/hello_world.war
