# stage-1
FROM amazoncorretto:11-alpine-jdk AS builder
WORKDIR /app/source
COPY . .

# 🔥 give execute permission
RUN chmod +x mvnw

RUN ./mvnw clean package -Dspring.profiles.active=build -DskipTests

# stage-2
FROM amazoncorretto:11-alpine-jdk
COPY --from=builder /app/source/target/*.jar /app/app.jar
EXPOSE 8082
CMD ["java", "-jar", "/app/app.jar"]
