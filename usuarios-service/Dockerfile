# Etapa de compilación
FROM maven:3.9.4-eclipse-temurin-21 AS build
WORKDIR /build

COPY ../ .

RUN mvn -pl usuarios-service -am clean package -DskipTests

# Etapa de ejecución
FROM eclipse-temurin:21-jdk-alpine
WORKDIR /app
COPY --from=build /build/usuarios-service/target/*.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]