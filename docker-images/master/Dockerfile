FROM jenkinsci/jenkins:latest

RUN /usr/local/bin/install-plugins.sh docker-plugin pipeline-maven nexus-jenkins-plugin docker-workflow email-ext build-pipeline-plugin git-parameter github-oauth nexus-artifact-uploader workflow-aggregator sonar ssh credentials-binding
RUN rm -rf /var/jenkins_home/config.xml
ADD config.xml /var/jenkins_home
RUN rm -rf /var/jenkins_home/credentials.xml
ADD credentials.xml /var/jenkins_home
RUN bash -c 'mkdir -p /var/jenkins_home/Vagrant'
ADD node.xml /var/jenkins_home/nodes/Vagrant



ENV JENKINS_USER admin
ENV JENKINS_PASS admin

# Skip initial setup
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

COPY executors.groovy /usr/share/jenkins/ref/init.groovy.d/
COPY default-user.groovy /usr/share/jenkins/ref/init.groovy.d/

VOLUME /var/jenkins_home
