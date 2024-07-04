## Pull JDK Dev Image to Use as Builder Image
FROM cgr.dev/chainguard/jdk:latest-dev as build

WORKDIR /opt/app

COPY . .

# Run maven
RUN ./mvnw clean install

# Use JRE Image to run artifacts producded by JDK Build stage
FROM cgr.dev/chainguard/jre:latest-dev

WORKDIR /opt/app

# Copy Jars from biuld stage
COPY --from=build /opt/app/target/*.jar /opt/app/*.jar
ENTRYPOINT ["java", "-jar", "/opt/app/*.jar" ]