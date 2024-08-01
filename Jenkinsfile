node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'sq-1';
    withSonarQubeEnv() {
      sh "usr/local/bin/sonar-scanner"
    }
  }
}
