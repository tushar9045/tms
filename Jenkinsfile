pipeline {
    agent any
<<<<<<< HEAD
     parameters {
        choice(name: 'BRANCH_NAME', choices: ['main', 'test', 'dev'], description: 'Branch to build')
=======
    environment {
        SONAR_HOST_URL = 'http://3.109.186.253:9000'
        SONAR_PROJECT_KEY = 'test-2'
        SONAR_AUTH_TOKEN = 'sqp_668112afa5bad0fa29e612f3b2e637780fb30336'
        PATH+EXTRA = '/path/to/your/sonar-scanner/bin:$PATH'
>>>>>>> 700bad2 (xyz)
    }
    stages {
<<<<<<< HEAD
        stage('SCM') {
            steps {
                checkout([$class: 'GitSCM',
                        branches: [[name: "${params.BRANCH_NAME}"]],
                        userRemoteConfigs: scm.userRemoteConfigs
                    ])
=======
        stage('Checkout') {
            steps {
                checkout scm
>>>>>>> 700bad2 (xyz)
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sq-1') {
<<<<<<< HEAD
                    sh '/opt/sonar-scanner/bin/sonar-scanner -Dsonar.projectKey=test -Dsonar.sources=TMS'
                }
            }
        }
        
=======
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
       
>>>>>>> 700bad2 (xyz)
    }
}
