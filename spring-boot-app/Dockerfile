FROM adoptopenjdk/maven-openjdk11:latest AS builder

WORKDIR /opt/app

COPY . .

RUN mvn clean package

# You can change this base image to anything else
# But make sure to use the correct version of Java

FROM adoptopenjdk/openjdk11:alpine-jre

WORKDIR /opt/app

COPY --from=builder /opt/app/target/spring-boot-web.jar /opt/app/spring-boot-web.jar

USER nobody

# This should not be changed
ENTRYPOINT ["java","-jar","spring-boot-web.jar"]
