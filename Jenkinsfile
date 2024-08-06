pipeline {
    agent any

    tools {
        sonarQubeScanner 'SonarQube Scanner'
    }

    stages {
        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarQube Scanner'
                    withSonarQubeEnv('SonarQube') {
                        sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=my-php-project -Dsonar.sources=. > ${WORKSPACE}/plan.txt"
                    }
                }
            }
        }

       
    }
}
