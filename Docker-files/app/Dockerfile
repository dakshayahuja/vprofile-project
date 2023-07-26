FROM openjdk:11 AS build
RUN apt update && apt install -y maven
RUN git clone https://github.com/dakshayahuja/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11 
LABEL "Project" = "Vprofile"
LABEL "Author" = "Dakshay"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]