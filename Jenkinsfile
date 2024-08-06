pipeline {
    agent any

    stages {
        
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQubeServer') {
                   sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=test -Dsonar.sources=TMS"
                }
            }
        }
        stage('Quality Gate') {
            steps {
                script {
                    timeout(time: 1, unit: 'HOURS') {
                        def qg = waitForQualityGate()
                        writeFile file: 'quality-gate-result.txt', text: "Quality Gate Status: ${qg.status}\n"
                         if (qg.status == 'OK') {
                            echo 'pappu pass ho gaya'
                        } else {
                            error "Pipeline aborted due to quality gate failure: ${qg.status}"
                        }
                    }
                }
            }
        }
        stage('Save SonarQube Output') {
            steps {
                script {
                    def sonarOutput = readFile 'quality-gate-result.txt'
                    writeFile file: 'sonar-analysis-result.txt', text: sonarOutput
                }
            }
        }
    }
}
