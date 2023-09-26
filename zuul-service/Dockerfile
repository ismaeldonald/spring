FROM adoptopenjdk/openjdk11:jre-11.0.6_10-alpine

WORKDIR /app

COPY ./target/zuul-service-0.0.1-SNAPSHOT.jar .

EXPOSE 8090

ENTRYPOINT ["java", "-jar", "zuul-service-0.0.1-SNAPSHOT.jar"]