pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64'
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
    }

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
                    // Check the Java version used by SonarScanner
                    sh 'java --version'

                    // Run the SonarQube scanner for PHP
                    sh '''
                    /opt/sonar-scanner/bin/sonar-scanner \
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
