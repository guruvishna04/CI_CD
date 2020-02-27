FROM jenkins/jenkins:lts

COPY certs/github.cer /usr/share/jenkins/certs/github.cer

#ENV JENKINS_USER admin
#ENV JENKINS_PASS admin

# Skip initial setup
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false -Djavax.net.ssl.trustStore=$JAVA_HOME/jre/lib/security/cacert -Djavax.net.ssl.trustStorePassword=changeit

USER root
RUN keytool -import -alias fev-github -keystore $JAVA_HOME/jre/lib/security/cacerts -file  /usr/share/jenkins/certs/github.cer -storepass changeit -noprompt
#COPY plugins.txt /usr/share/jenkins/plugins.txt
#RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/plugins.txt
USER jenkins
RUN git config --global http.sslverify "false" 