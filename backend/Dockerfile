# Stage 1: Build the application
FROM maven:3.8.4-openjdk-17 AS build
WORKDIR /app
COPY . .
RUN mvn clean package

# Stage 2: Create the production image
FROM openjdk:17-jdk-slim
EXPOSE 9000
WORKDIR /app
COPY --from=build /backend/src/main/java/com/keyoola/BackendApplication.war app.war
ENTRYPOINT ["java", "-jar", "app.war"]
