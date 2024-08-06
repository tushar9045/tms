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
                        sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=my-php-project -Dsonar.sources=."
                    }
                }
            }
        }

        stage('Capture Output') {
            steps {
                script {
                    def sonarOutput = sh(script: "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=my-php-project -Dsonar.sources=.", returnStdout: true).trim()
                    writeFile file: "${WORKSPACE}/plan.txt", text: sonarOutput
                }
            }
        }
    }
}
