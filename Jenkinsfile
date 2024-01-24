pipeline {
    agent any
    environment {
        SCANNER_HOME = tool 'sonar_scanner'

   }

    stages {
            stage('SonarQube') {
             steps {
                withSonarQubeEnv('sonar') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=Microservice_Application -Dsonar.ProjectName=Microservice_Application -Dsonar.java.binaries=.'''
                }
            }
        }    
    }
}
