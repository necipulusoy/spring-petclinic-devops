# Build aşaması
FROM maven:3.8.6-openjdk-18 AS build
WORKDIR /app
COPY pom.xml .  # Pom.xml dosyasını kopyala
COPY src ./src  # src klasörünü kopyala
RUN mvn clean package -DskipTests  # Maven ile projeyi derle

# Uygulama aşaması
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY --from=build /app/target/spring-petclinic-*.jar /app/spring-petclinic.jar  # Build aşamasından çıkan jar dosyasını kopyala
ENTRYPOINT ["java", "-jar", "/app/spring-petclinic.jar"]  # Uygulamayı çalıştır
EXPOSE 8080  
