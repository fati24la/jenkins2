# Étape 1 : Build avec Maven + Eclipse Temurin
FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app

COPY ./pom.xml ./
COPY ./src ./src

RUN mvn clean package -DskipTests

# Étape 2 : Runtime
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app

COPY --from=builder /app/target/*.jar voiture-service.jar

EXPOSE 8089

ENTRYPOINT ["java", "-jar", "/app/voiture-service.jar"]
