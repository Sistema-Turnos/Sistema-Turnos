# Etapa de compilación
FROM maven:3.8.5-eclipse-temurin-17 AS build
WORKDIR /build

# Copiamos todo el proyecto desde la raíz para incluir el pom padre y los módulos
COPY ../ .

# Compilamos solo el módulo ordenes-service y sus dependencias
RUN mvn -pl ordenes-service -am clean package -DskipTests

# Etapa de ejecución
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY --from=build /build/ordenes-service/target/*.jar app.jar
EXPOSE 8083
ENTRYPOINT ["java", "-jar", "app.jar"]
