FROM maven:3.9.4-eclipse-temurin-21 AS build
WORKDIR /build
COPY . .
WORKDIR /build/administracion-service
RUN mvn clean package -DskipTests

FROM eclipse-temurin:21
WORKDIR /app
COPY --from=build /build/administracion-service/target/administracion-service.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
