pipeline {
  agent {
    docker {
      image 'docker:latest'
    }
  }
  stages {
    stage('Quality Check') {
      steps {
        sh 'ls -la $(pwd)'
        sh 'docker run --rm -v $(pwd):/root/src binhsonnguyen/sonarqube-scanner:1.0.3-alpha-3'
       }
    }
  }
}