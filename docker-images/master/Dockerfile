FROM jenkinsci/jenkins:latest

RUN /usr/local/bin/install-plugins.sh nexus-jenkins-plugin docker-workflow email-ext build-pipeline-plugin git-parameter github-oauth nexus-artifact-uploader workflow-aggregator sonar ssh credentials-binding


ENV JENKINS_USER admin
ENV JENKINS_PASS admin

# Skip initial setup
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

COPY executors.groovy /usr/share/jenkins/ref/init.groovy.d/
COPY default-user.groovy /usr/share/jenkins/ref/init.groovy.d/

VOLUME /var/jenkins_home
