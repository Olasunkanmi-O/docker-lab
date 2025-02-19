    # this image is been built to be used for the artifact after which the artifact will be copied off 
FROM maven:3.9.9-eclipse-temurin-21-jammy AS BUILD_IMAGE
    # this command is used to clone the source code from github 
RUN git clone https://github.com/hkhcoder/vprofile-project.git
    #the command is used to build the artifact using maven 
RUN cd /vprofile-project && git checkout containers && mvn install



FROM tomcat:10-jdk21
    #this command remove the default tomcat app after pulling the image 
RUN rm -rf /usr/local/tomcat/webapps/*
    #copy the artifact from the container process above and pasted where the default tomcat app should have been
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]

