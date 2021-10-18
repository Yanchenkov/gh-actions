FROM gradle:7.1-jdk11 AS build

COPY --chown=gradle:gradle . /home/gradle/src
WORKDIR /home/gradle/src
RUN gradle build --no-daemon


FROM bellsoft/liberica-openjdk-debian:11.0.12

RUN groupadd -r spring \
  && useradd --no-log-init -r -g spring spring \
  && mkdir /app \
  && chown -R spring:spring /app

USER spring:spring
WORKDIR /app
EXPOSE 5000

COPY --from=build /home/gradle/src/build/libs/*.jar /app/main.jar

ENTRYPOINT ["java","-jar","main.jar"]
