FROM qameta/jenkins-slave:base

RUN apt-get update \
    && apt-get install -y --no-install-recommends curl \
    && curl -sSL https://get.rvm.io | sudo bash -s stable --ruby

RUN usermod -a -G rvm jenkins

RUN /usr/local/rvm/bin/rvm alias create ruby ruby
RUN echo "export PATH=/usr/local/rvm/rubies/ruby/bin:$PATH" >> /home/jenkins/.bashrc