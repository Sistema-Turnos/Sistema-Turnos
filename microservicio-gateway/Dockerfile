# Primera etapa: Construcción con Maven
FROM maven:3.9.4-eclipse-temurin-21 AS build
WORKDIR /build
COPY . .
WORKDIR /build/microservicio-gateway
RUN mvn clean package -DskipTests

# Segunda etapa: Imagen final
FROM eclipse-temurin:21
WORKDIR /app
COPY --from=build /build/microservicio-gateway/target/*.jar app.jar

# Puertos y variables de entorno
EXPOSE 8080
EXPOSE 9090

# Health check
HEALTHCHECK --interval=30s --timeout=3s \
    CMD curl -f http://localhost:8080/actuator/health || exit 1

ENTRYPOINT ["java", "-jar", "app.jar"]