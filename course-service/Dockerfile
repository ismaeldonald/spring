FROM maven:3.8-openjdk-11-slim AS build

WORKDIR /app

COPY pom.xml .

RUN mvn dependency:go-offline -B

COPY src ./src

RUN mvn package -DskipTests


FROM adoptopenjdk/openjdk11:jre-11.0.6_10-alpine

WORKDIR /app

COPY --from=build /app/target/course-service-0.0.1-SNAPSHOT.jar .

EXPOSE 8761

ENTRYPOINT ["java", "-jar", "course-service-0.0.1-SNAPSHOT.jar"]