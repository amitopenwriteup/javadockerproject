# Multi-stage build for Java 11 Examples Project
FROM openjdk:11-jdk-slim

WORKDIR /app

# Install Maven
RUN apt-get update && \
    apt-get install -y maven 

# Copy Maven files and download dependencies
COPY pom.xml .
RUN mvn dependency:resolve

# Copy source and build
COPY src ./src
RUN mvn clean package -DskipTests

# Expose port
EXPOSE 8080

# Run the application
ENTRYPOINT ["java", "-jar", "app.jar"]
