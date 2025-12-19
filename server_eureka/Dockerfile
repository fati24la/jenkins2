# Étape 1 : Build avec Maven + Eclipse Temurin
FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app

COPY ./pom.xml ./
COPY ./src ./src

RUN mvn clean package -DskipTests

# Étape 2 : Runtime avec Java 17
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app

COPY --from=builder /app/target/*.jar eureka-server.jar

EXPOSE 8761

ENTRYPOINT ["java", "-jar", "/app/eureka-server.jar"]
