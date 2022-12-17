FROM amazoncorretto:17-alpine3.15-jdk

# Datadog agent installation
#RUN apk --no-cache add curl && curl -s -L -o /dd-java-agent.jar "https://dtdg.co/latest-java-tracer"
ADD target/order-service-0.0.1-SNAPSHOT.jar /app/order-service-0.0.1-SNAPSHOT.jar
COPY postgre.jks /tmp/postgre.jks
WORKDIR /app
EXPOSE 8082

ADD https://github.com/open-telemetry/opentelemetry-java-instrumentation/releases/download/v1.21.0/opentelemetry-javaagent.jar /app/opentelemetry-javaagent.jar
ENV JAVA_TOOL_OPTIONS=-javaagent:/app/opentelemetry-javaagent.jar

ENTRYPOINT ["java", "-jar", "/app/order-service-0.0.1-SNAPSHOT.jar"]
