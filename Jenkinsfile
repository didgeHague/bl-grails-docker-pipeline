def app;
def pwd = pwd()
String commit_id;

String env = "staging";
String tagName;
String imageName = "grails-jenkins-pipeline";
String serviceName = "gjp2_app"
String grailsDocker = "proactivehk/grails:3.2.7"

pipeline {
    agent none
    stages {
         stage('Checkout') {
            steps {
                checkout scm
                sh "git rev-parse HEAD > .git/commit-id"
            }
        }

        stage('Test app') {
          agent{
            docker {
              image $grailsDocker
              args '-v $pwd:/app'
           }
          }
            steps {
                sh 'grails test-app'
            }
        }
    }
}
