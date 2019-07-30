FROM jre:latest
VOLUME /tmp
COPY ./app.jar app.jar
EXPOSE 8080 
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
