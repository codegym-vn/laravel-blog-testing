pipeline {
  agent {
    docker { image 'docker:rc' }
  }

  environment {
    QUALITY_CHECK = 'true'
  }

  stages {
    stage('Test') {
      steps {
        sh 'docker -v'
        sh 'pwd'
        sh 'ls'
        sh 'ping http://scrumlab.agilead.vn'
        sh 'docker run -v $PWD:/root/src binhsonnguyen/sonarqube-scanner'
      }
    }
  }
  post {
    always {
      echo 'This will always run'
      deleteDir() /* clean up our workspace */
    }
    success {
      echo 'This will run only if successful'
    }
    failure {
      echo 'This will run only if failed'
    }
    unstable {
      echo 'This will run only if the run was marked as unstable'
    }
    changed {
      echo 'This will run only if the state of the Pipeline has changed'
      echo 'For example, if the Pipeline was previously failing but is now successful'
    }
  }
}