FROM qameta/jenkins-slave:base

RUN apt-get update \
    && apt-get install -y --no-install-recommends curl \
    && curl -L https://get.rvm.io | bash -s stable --ruby

RUN /bin/bash -c "source /etc/profile.d/rvm.sh"
