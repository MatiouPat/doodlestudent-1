# Build stage #
FROM maven:3.8.4-jdk-11-slim AS build
WORKDIR /home/app
COPY src ./
COPY pom.xml .
#RUN mvn -f pom.xml package
RUN mvn -f pom.xml clean package -Dquarkus.package.type=uber-jar


# Package stage #
FROM openjdk:11-jre-slim
COPY --from=build /home/app/target/tlcdemoApp-1.0.0-SNAPSHOT-runner.jar /usr/local/lib/doodlestudent/api.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/usr/local/lib/doodlestudent/api.jar"]