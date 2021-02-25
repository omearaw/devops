mkdir -p $HOME/playground/jcasc
cd $HOME/playground/jcasc
vi $HOME/playground/jcasc/Dockerfile
    FROM jenkins/jenkins:latest
    ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
docker build -t jenkins:jcasc