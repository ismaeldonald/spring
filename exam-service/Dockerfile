FROM openjdk:11-ea-11-jdk-slim

WORKDIR /app

COPY ./target/exam-service-0.0.1-SNAPSHOT.jar .

EXPOSE 8082

ENTRYPOINT ["java", "-jar", "exam-service-0.0.1-SNAPSHOT.jar"]

