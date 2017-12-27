pipeline {
  agent any

  environment {
    QUALITY_CHECK = 'true'
  }

  stages {
    stage('Warmup') {
      steps {
        sh 'printenv'
        sh 'docker -v'
        sh 'pwd'
        sh 'ls -lha'
        sh 'ping -c4 scrumlab.agilead.vn'
      }
    }

    stage('Quality Check') {
      steps {
        sh 'ls -la $(pwd)'
        sh 'touch .foo'
        sh 'docker run --rm -v $(pwd):/root/src binhsonnguyen/sonarqube-scanner:1.0.3-alpha-3'
        sh 'cat .scannerwork/report-task.txt'
      }
    }
  }

  post {
    always {
      echo 'POST: clean up our workspace'
    }
    success {
      echo 'POST: success'
    }
    failure {
      echo 'POST: failed'
    }
    unstable {
      echo 'POST: unstable'
    }
    changed {
      echo 'POST: changed'
    }
  }
}