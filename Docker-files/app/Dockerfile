# Build Stage - Compile Java Artifact
FROM maven:3.9.9-eclipse-temurin-21-jammy AS BUILD_IMAGE
# specify a working directory
WORKDIR /app
# clone the source code 
RUN git clone --branch containers https://github.com/Olasunkanmi-O/vprofile-project.git
# change directory into the cloned directory
WORKDIR /app/vprofile-project
RUN mvn install


# Runtime Stage - Deploy to Tomcat
FROM tomcat:10-jdk21
# remove the default tomcat application 
RUN rm -rf /usr/local/tomcat/webapps/*
# copy the artifact to the tomcat directory
COPY --from=BUILD_IMAGE /app/vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080

CMD ["catalina.sh", "run"]

