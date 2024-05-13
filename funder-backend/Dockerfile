# FROM maven:3.8.3-openjdk-17 AS build
# COPY . /home/app
# WORKDIR /home/app
# RUN mvn -f /home/app/pom.xml clean install

# FROM openjdk:17-jdk-slim
# COPY --from=build /home/app/target/funder-backend-0.0.1-SNAPSHOT.jar /app/funder-backend.jar
# EXPOSE 8080
# ENTRYPOINT ["java", "-jar", "/app/funder-backend.jar"]

FROM maven:3.8.4-openjdk-17 AS build

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests

FROM openjdk:17-jdk-slim

EXPOSE 8080

COPY --from=build /app/target/funder-backend-0.0.1-SNAPSHOT.jar /app/funder-backend.jar

ENTRYPOINT ["java", "-jar", "/app/funder-backend.jar"]
