FROM tomcat:9.0
RUN mv /usr/local/tomcat/webapps.dist/* /usr/local/tomcat/webapps/
RUN rm -f /usr/local/tomcat/conf/tomcat-users.xml
COPY tomcat-users.xml /usr/local/tomcat/conf/
CMD ["catalina.sh","run"]
