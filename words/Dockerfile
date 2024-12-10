# Build stage
FROM maven:3.8.1-openjdk-11-slim AS builder

# Set working directory
WORKDIR /app

# Copy pom.xml and source code
COPY pom.xml .
COPY src ./src

# Build the application and copy dependencies
RUN mvn clean package dependency:copy-dependencies

# Runtime stage
FROM openjdk:11-jre-slim

WORKDIR /app

# Copy the jar and its dependencies 
COPY --from=builder /app/target/words.jar .
COPY --from=builder /app/target/dependency ./dependency

# Set environment variables for the database connection
ENV DB_URL=jdbc:postgresql://db:5432/wordsmith
ENV DB_USER=postgres 
ENV DB_PASSWORD=postgres

# Expose port 8080
EXPOSE 8080

# Run the application
CMD ["java", "-cp", "words.jar:dependency/*", "Main"]