# docker_tomcat
1

It turns out that all default tomcat apps have been removed from the webapps directory for all tomcat images starting with Tomcat version 7. All apps have been moved to /usr/local/tomcat/webapps.dist directory so that they are not launched by default. You can read about it here.

If you still want to access those default apps you can copy them back to the webapps directory, if you wish:

FROM tomcat:9.0
RUN mv /usr/local/tomcat/webapps.dist/* /usr/local/tomcat/webapps/
CMD ["catalina.sh","run"]
or copy only the apps that you want. Also you will have to edit tomcat configuration files to not get 403 when accessing those apps.
