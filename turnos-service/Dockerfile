# Etapa de compilación
FROM maven:3.9.4-eclipse-temurin-21 AS build
WORKDIR /build

# Copiamos todo el proyecto desde la raíz para incluir el pom padre y los módulos
COPY ../ .

# Compilamos solo el módulo ordenes-service y sus dependencias
RUN mvn -pl turnos-service -am clean package -DskipTests

# Etapa de ejecución
FROM eclipse-temurin:21-jdk-alpine
WORKDIR /app
COPY --from=build /build/turnos-service/target/*.jar app.jar
EXPOSE 8083
ENTRYPOINT ["java", "-jar", "app.jar"]
