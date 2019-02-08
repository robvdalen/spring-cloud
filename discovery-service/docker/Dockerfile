FROM openjdk:11-jdk-slim

LABEL maintainer="Vdalen"
LABEL os="centos"
LABEL container="docker"
LABEL language="java"

# set correct timezone
ENV TZ Europe/Amsterdam

ENV DEFAULT_JAVA_OPTS="-Djava.security.egd=file:/dev/./urandom"
ENV _JAVA_OPTIONS=${JAVA_OPTS:-""}
ENV JAVA_OPTS=${_JAVA_OPTIONS}
ENV APPLICATION_HOME=/application

RUN mkdir -p ${APPLICATION_HOME}

WORKDIR ${APPLICATION_HOME}

EXPOSE 8761

# Add data to the docker container
ADD ${project.build.finalName}.${project.packaging} ${APPLICATION_LINK}/${project.artifactId}.${project.packaging}

ENTRYPOINT exec java ${JAVA_OPTS} ${DEFAULT_JAVA_OPTS} -jar ${APPLICATION_LINK}/${project.artifactId}.${project.packaging}