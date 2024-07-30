pipeline {
    agent any

    tools {
        // Define SonarQube Scanner installation
        sonarQubeScanner 'SonarQube Scanner'
    }

    stages {
        stage('SonarQube Analysis') {
            steps {
                script {
                    // Run SonarQube Scanner with appropriate configuration
                    def scannerHome = tool 'SonarQube Scanner'
                    withSonarQubeEnv('SonarQube') {
                        sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=my-php-project -Dsonar.sources=."
                    }
                }
            }
        }

        stage('Quality Gate') {
            steps {
                // Wait for the SonarQube analysis to complete and check the Quality Gate status
                timeout(time: 1, unit: 'HOURS') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}

