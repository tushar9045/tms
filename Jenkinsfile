
pipeline {
    agent any
    environment {
        SONAR_HOST_URL = 'http://3.109.186.253:9000'
        SONAR_PROJECT_KEY = 'test-2'
        SONAR_AUTH_TOKEN = 'sqp_668112afa5bad0fa29e612f3b2e637780fb30336'
        PATH+EXTRA = '/usr/local/bin/sonar-scanner/bin:$PATH'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sq-1') {
                    sh '''
                        sonar-scanner \
                        -Dsonar.projectKey=${SONAR_PROJECT_KEY} \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=${SONAR_HOST_URL} \
                        -Dsonar.login=${SONAR_AUTH_TOKEN}
                    '''
                }
            }
        }
       
    }
}

