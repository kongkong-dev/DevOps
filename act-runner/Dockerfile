
# Use the base image from Gitea runner
FROM gitea/runner-images:ubuntu-22.04

# Set environment variables
ENV APP_HOME=/app
ENV JAVA_HOME=/usr/lib/jvm/jdk-21.0.2+13
ENV GRADLE_USER_HOME=/home/mydata/.gradle


# Install dependencies
RUN apt-get update && \
    apt-get install -y wget unzip

# Install Eclipse Temurin JDK 21
RUN mkdir -p /usr/lib/jvm && \
    wget -O /tmp/temurin-21-jdk.tar.gz https://github.com/adoptium/temurin21-binaries/releases/download/jdk-21.0.2+13/OpenJDK21U-jdk_x64_linux_hotspot_21.0.2_13.tar.gz && \
    tar -xzf /tmp/temurin-21-jdk.tar.gz -C /usr/lib/jvm && \
    rm /tmp/temurin-21-jdk.tar.gz && \
    ln -s /usr/lib/jvm/jdk-21.0.2+13/bin/java /usr/bin/java && \
    ln -s /usr/lib/jvm/jdk-21.0.2+13/bin/javac /usr/bin/javac

# Add Java binaries to PATH
ENV PATH=$JAVA_HOME/bin:$PATH

# Install Gradle 8.7
RUN wget -O /tmp/gradle.zip https://services.gradle.org/distributions/gradle-8.7-bin.zip && \
    unzip /tmp/gradle.zip -d /opt && \
    rm /tmp/gradle.zip && \
    ln -s /opt/gradle-8.7 /opt/gradle && \
    ln -s /opt/gradle/bin/gradle /usr/bin/gradle

# Create non-root user and set ownership
RUN groupadd --gid 1001 mydata && \
    useradd -g 1001 -u 1001 -s /bin/bash -d /home/mydata -m mydata && \
    chown -R mydata:mydata /home/mydata && \
    mkdir -p ${APP_HOME} && \
    chown -R mydata:mydata ${APP_HOME} && \
    chown -R mydata:mydata /usr/lib/jvm/jdk-21.0.2+13 && \
    mkdir -p ${APP_HOME} ${GRADLE_USER_HOME} && \
    chown -R mydata:mydata ${APP_HOME} ${GRADLE_USER_HOME} && \
    chown -R mydata:mydata /opt/gradle-8.7 

WORKDIR ${APP_HOME}

# Switch to non-root user
USER mydata

# Verify installations
RUN echo $JAVA_HOME && \
    echo $PATH && \
    java -version && \
    javac -version && \
    gradle -version
