       node {
    stage('SCM') {
        checkout scm
    }
    stage('SonarQube Analysis') {
        def scannerHome = tool 'sonar-scanner';
        withSonarQubeEnv() {
            sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=test -Dsonar.sources=TMS"
        }
    }
    stage('Quality Gate') {
        steps {
            script {
                def qualityGate = waitForQualityGate()
                if (qualityGate.status != 'OK') {
                    error "Pipeline aborted due to quality gate failure: ${qualityGate.status}"
                } else {
                    echo "Quality Gate passed: ${qualityGate.status}"
                }
            }
        }
    }
}
