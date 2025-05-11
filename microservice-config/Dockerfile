FROM maven:3.9.4-eclipse-temurin-21 AS build
WORKDIR /build
COPY . .
WORKDIR /build/microservice-config
RUN mvn clean package -DskipTests

FROM eclipse-temurin:21
WORKDIR /app
COPY --from=build /build/microservice-config/target/*.jar app.jar

EXPOSE 8888
ENTRYPOINT ["java", "-jar", "app.jar"]
