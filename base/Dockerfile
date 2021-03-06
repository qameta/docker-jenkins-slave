FROM ubuntu:14.04

# Setup locale
ENV LANG en_US.utf8
RUN locale-gen $LANG

# Install devtools
RUN \
  apt-get update && \
  apt-get install -y software-properties-common python-software-properties

# Install git
RUN \
  apt-add-repository -y ppa:git-core/ppa && \
  apt-get update && \
  apt-get install -y git

# Install oracle-java
RUN \
  echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
  add-apt-repository -y ppa:webupd8team/java && \
  apt-get update && \
  apt-get install -y oracle-java8-installer

ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

ENV JENKINS_HOME /home/jenkins

ENV user=jenkins
ENV group=jenkins
ENV uid=1000
ENV gid=1000

# Jenkins is run with user `jenkins`, uid = 1000
# If you bind mount a volume from the host or a data container, ensure you use the same uid
RUN groupadd -g ${gid} ${group} && \
    useradd -d "${JENKINS_HOME}" -u ${uid} -g ${gid} -m -s /bin/bash ${user}

# Jenkins .ssh and .gnupg directory is a volume
VOLUME ${JENKINS_HOME}/.gnupg
VOLUME ${JENKINS_HOME}/.ssh

# Install a basic SSH server
RUN \
  apt-get update && \
  apt-get install -y openssh-server

RUN sed -i 's|session    required     pam_loginuid.so|session    optional     pam_loginuid.so|g' /etc/pam.d/sshd
RUN mkdir -p /var/run/sshd

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]