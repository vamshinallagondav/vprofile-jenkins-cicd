FROM tomcat:8-jre11

RUN RM -RF /USR/LOCAL/tomcat/webapps/*

COPY target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh" ,"run"]
