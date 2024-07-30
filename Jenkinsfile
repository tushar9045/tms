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
                    // Run the SonarQube scanner for PHP
                    sh '''
                    sonar-scanner \
                        -Dsonar.projectKey=s \
                        -Dsonar.projectName="s" \
                        -Dsonar.host.url=http://52.66.236.10:9000 \
                        -Dsonar.sources=.
                    '''
                    echo 'SonarQube Analysis Completed'
                }
            }
        }
    }
}
