FROM qameta/jenkins-slave:base

# Install Maven.
ENV MAVEN_VERSION 3.3.9
RUN \
  wget  -O /tmp/maven.tar.gz http://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz && \
  tar -xzf /tmp/maven.tar.gz -C /tmp && \
  mv /tmp/apache-maven-$MAVEN_VERSION /usr/share/maven && \
  ln -sf /usr/share/maven/bin/mvn /usr/bin/mvn
ENV MAVEN_HOME /usr/share/maven

VOLUME ${JENKINS_HOME}/.m2