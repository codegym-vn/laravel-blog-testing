pipeline {
  agent {
    docker { image 'docker:rc' }
  }

  stages {
    stage('Quality Check') {
      steps {
        sh 'docker run -v $PWD:/root/src binhsonnguyen/sonarqube-scanner'
      }
    }
  }
}