FROM maven:3.9.9-eclipse-temurin-17 AS build

WORKDIR /workspace

COPY pom.xml pom.xml
RUN mvn -DskipTests dependency:go-offline

COPY src src
RUN mvn -DskipTests package

FROM tomcat:10.1-jre17-temurin

COPY --from=build /workspace/target/beeton-swap-api.war /usr/local/tomcat/webapps/beeton-swap-api.war

EXPOSE 8080
