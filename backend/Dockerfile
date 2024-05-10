# Stage 1: Build the application
FROM maven:3.8.4-openjdk-17 AS build
WORKDIR /backend
COPY . .
RUN mvn clean package

# Stage 2: Create the production image
FROM openjdk:17-jdk-slim
EXPOSE 9000
WORKDIR /backend
COPY --from=build /src/main/java/com/keyoola/BackendApplication.war app.war
ENTRYPOINT ["java", "-jar", "app.war"]
