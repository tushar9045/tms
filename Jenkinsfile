pipeline {
    agent any
     parameters {
        choice(name: 'BRANCH_NAME', choices: ['main', 'test', 'dev'], description: 'Branch to build')
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
                withSonarQubeEnv('sq-1') {
                    sh '/opt/sonar-scanner/bin/sonar-scanner -Dsonar.projectKey=test -Dsonar.sources=TMS'
                }
            }
        }
        
    }
}
