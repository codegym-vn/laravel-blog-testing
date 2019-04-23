pipeline {
  agent {
    docker {
      image 'docker:latest'
    }
    
  }
  stages {
    stage('sona') {
      steps {
        waitForQualityGate()
      }
    }
  }
}