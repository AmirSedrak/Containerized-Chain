FROM jenkins/jenkins:lts

USER root

RUN apt-get update && \
    apt-get install -y \
        python3 \
        python3-pip \
        python3-setuptools \
        groff \
        git \
        curl \
        less \
        postgresql \
    && pip3 install --upgrade pip \
    && apt-get clean

RUN pip3 --no-cache-dir install --upgrade awscli

USER jenkins

ENV JAVA_OPTS="-Djenkins.install.runSetupWizard=false" \
    JENKINS_URL=http://localhost\
    JENKINS_USER=admin \
    JENKINS_PASS=admin 


COPY plugins.txt /usr/share/jenkins/ref/plugins.txt


RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt
