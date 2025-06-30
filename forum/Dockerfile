# Stage 1: Build
FROM openjdk:24-jdk-slim as builder

WORKDIR /app

COPY . .

RUN ./gradlew bootJar

# Stage 2: Run
FROM openjdk:24-jdk-alpine

WORKDIR /app

COPY --from=builder /app/build/libs/*.jar app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]