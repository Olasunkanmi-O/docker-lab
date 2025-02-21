# Build Stage - Compile Java Artifact
FROM maven:3.9.9-eclipse-temurin-21-jammy AS BUILD_IMAGE
WORKDIR /app
RUN git clone --branch containers https://github.com/Olasunkanmi-O/vprofile-project.git
WORKDIR /app/vprofile-project
RUN mvn install

# Runtime Stage - Deploy to Tomcat
FROM tomcat:10-jdk21
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE /app/vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080

CMD ["catalina.sh", "run"]

