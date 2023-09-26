FROM openjdk:11-ea-11-jdk-slim

WORKDIR /app

COPY ./target/user-service-0.0.1-SNAPSHOT.jar .

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "user-service-0.0.1-SNAPSHOT.jar"]

