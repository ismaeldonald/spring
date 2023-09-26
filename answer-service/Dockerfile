FROM openjdk:11-ea-11-jdk-slim

WORKDIR /app

COPY ./target/answer-service-0.0.1-SNAPSHOT.jar .

EXPOSE 8083

ENTRYPOINT ["java", "-jar", "answer-service-0.0.1-SNAPSHOT.jar"]

