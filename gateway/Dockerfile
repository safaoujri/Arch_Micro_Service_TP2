# Étape 1 : Utilisation de l'image Maven pour construire le projet
FROM maven:3.8.4-openjdk-17 AS builder
WORKDIR /app
COPY ./src ./src
COPY ./pom.xml .
RUN mvn clean package

# Étape 2 : Utilisation de l'image OpenJDK pour exécuter l'application
FROM openjdk:17-jdk-alpine
VOLUME /tmp
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} gateway-service.jar

# Lancer l'application avec Java
ENTRYPOINT ["java", "-jar", "/gateway-service.jar"]
