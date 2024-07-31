pipeline {
    agent any

 

    stages {
        stage('Git Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/tushar9045/tms']])
                echo 'Git Checkout Completed'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sq-1') {
                    // Ensure SonarScanner uses Java 17
                    sh '''
                         /usr/local/sonar-scanner/bin/sonar-scanner -Dsonar.projectKey=test-2 -Dsonar.sources=. -Dsonar.host.url=http://3.109.186.253:9000 -Dsonar.login=sqp_668112afa5bad0fa29e612f3b2e637780fb30336
                   
                    
                    '''
                    echo 'SonarQube Analysis Completed'
                }
            }
        }
    }
}
