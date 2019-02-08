FROM openjdk:11-jdk-slim

LABEL maintainer="Vdalen"
LABEL os="openjdk:11-jdk-slim"
LABEL container="docker"
LABEL language="java"

# set correct timezone
ENV TZ Europe/Amsterdam

ENV DEFAULT_JAVA_OPTS="-Djava.security.egd=file:/dev/./urandom"
ENV _JAVA_OPTIONS=${JAVA_OPTS:-""}
ENV JAVA_OPTS=${_JAVA_OPTIONS}
ENV USER_ID=500
ENV USER_NAME=docker
ENV APPLICATION_HOME=/home/${USER_NAME}/application

#adding user
RUN useradd -mu 500 docker
USER ${USER_NAME}
WORKDIR /home/${USER_NAME}

RUN mkdir ${APPLICATION_HOME} && chown ${USER_NAME}:${USER_NAME} ${APPLICATION_HOME}

WORKDIR ${APPLICATION_HOME}

EXPOSE 8761

# Add data to the docker container
ADD --chown=docker:docker ${project.build.finalName}.${project.packaging} ${APPLICATION_HOME}/${project.artifactId}.${project.packaging}

ENTRYPOINT exec java ${JAVA_OPTS} ${DEFAULT_JAVA_OPTS} -jar ${APPLICATION_HOME}/${project.artifactId}.${project.packaging}