FROM tomcat:9.0
RUN mv /usr/local/tomcat/webapps.dist/* /usr/local/tomcat/webapps/
RUN rm -f /usr/local/tomcat/conf/tomcat-users.xml
RUN rm -f /usr/local/tomcat/webapps/manager/META-INF/context.xml
COPY tomcat-users.xml /usr/local/tomcat/conf/
COPY context.xml /usr/local/tomcat/webapps/manager/META-INF/context.xml
COPY hello-world-war-1.0.0.war /usr/local/tomcat/webapps/hello-world-war-1.0.0.war
CMD ["catalina.sh","run"]
