FROM amazoncorretto:17-alpine3.15-jdk

# Datadog agent installation
#RUN apk --no-cache add curl && curl -s -L -o /dd-java-agent.jar "https://dtdg.co/latest-java-tracer"
ADD target/customer-service-bff-0.0.1-SNAPSHOT.jar /app/customer-service-bff-0.0.1-SNAPSHOT.jar
WORKDIR /app
EXPOSE 8080

ADD https://github.com/open-telemetry/opentelemetry-java-instrumentation/releases/download/v1.21.0/opentelemetry-javaagent.jar /app/opentelemetry-javaagent.jar
ENV JAVA_TOOL_OPTIONS=-javaagent:/app/opentelemetry-javaagent.jar

ENTRYPOINT ["java", "-jar", "/app/customer-service-bff-0.0.1-SNAPSHOT.jar"]
