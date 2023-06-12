FROM openjdk:11 AS BUILD_IMAGE
LABEL "project"="Vprofile"
LABEL "Author"="Awong"
RUN apt update && apt install maven -y
RUN git clone https://github.com/Nnange/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM  tomcat:9-jre11 
RUN  rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webaps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
