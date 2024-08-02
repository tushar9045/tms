pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                checkout scm
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sq-1') {
                    sh '/opt/sonar-scanner/bin/sonar-scanner -Dsonar.projectKey=test -Dsonar.sources=TMS'
                }
            }
        }
        
    }
}
