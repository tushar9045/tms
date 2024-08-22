pipeline {
    agent any

    parameters {
        choice(name: 'BRANCH_NAME', choices: ['main', 'test', 'dev'], description: 'Branch to build')
    }
    environment {
        SONAR_PROJECT_KEY = "chow"
    }

    stages {

        stage('SCM') {
            steps {
                checkout([$class: 'GitSCM',
                        branches: [[name: "${params.BRANCH_NAME}"]],
                        userRemoteConfigs: scm.userRemoteConfigs
                    ])
            }
        }    
        
        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'sonar-scanner'
                    withSonarQubeEnv('sq-1') {
                        sh "${scannerHome}/bin/sonar-scanner \
                            -Dsonar.projectKey=${SONAR_PROJECT_KEY} \
                            -Dsonar.sources=. \
                            -Dsonar.host.url=${SONAR_HOST} \
                            -Dsonar.login=${SONAR_AUTH_TOKEN}"
                    }
                }
            }
        }
    }
}
