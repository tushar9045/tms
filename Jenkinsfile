pipeline {
    agent any
    tools {
        maven 'Maven'
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
                withSonarQubeEnv('ServerNameSonar') {
                    bat '''mvn clean verify sonar:sonar -Dsonar.projectKey=ProjectNameSonar -Dsonar.projectName='ProjectNameSonar' -Dsonar.host.url=http://52.66.236.10:9000''' //port 9000 is default for sonar
                    echo 'SonarQube Analysis Completed'
                }
            }
        }
    }
}
