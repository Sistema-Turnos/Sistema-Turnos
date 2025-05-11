# Etapa 1: compilar con Maven
FROM maven:3.9.4-eclipse-temurin-21 AS build
WORKDIR /build
COPY . .
WORKDIR /build/microservicio-eureka
RUN mvn clean package -DskipTests

# Etapa 2: imagen final para ejecutar
FROM eclipse-temurin:21
WORKDIR /app
COPY --from=build /build/microservicio-eureka/target/*.jar app.jar

EXPOSE 8761
ENTRYPOINT ["java", "-jar", "app.jar"]
