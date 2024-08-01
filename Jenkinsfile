        node {
          stage('SCM') {
            checkout scm
          }
          stage('SonarQube Analysis') {
            def scannerHome = tool 'sq-1';
            withSonarQubeEnv() {
              sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=test -Dsonar.sources=TMS"
            }
          }
        }

