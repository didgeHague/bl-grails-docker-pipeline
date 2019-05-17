def app;
// def pwd = pwd()
String commit_id;

String env = "staging";
String tagName;
String imageName = "grails-jenkins-pipeline";
String serviceName = "gjp2_app"
String grailsDocker = "proactivehk/grails:3.2.7"

pipeline {
    agent any
    stages {
         stage('Checkout') {
            steps {
                checkout scm
                sh "git rev-parse HEAD > .git/commit-id"
                // commit_id = readFile('.git/commit-id').trim().take(7)
                // tagName = "${commit_id}-${env}"
            }
        }

        stage('Test app') {
          agent{
            docker {
              image 'proactivehk/grails:3.2.7'
              args '-v $pwd():/app'
           }
          }
            steps {
                sh 'grails test-app'
            }
        }
    }
}
