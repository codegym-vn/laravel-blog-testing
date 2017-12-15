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
        sh 'java -version'
        sh 'pwd'
        sh 'ls'
        sh 'ping -c4 scrumlab.agilead.vn'
      }
    }

    stage('Quality Check') {
      steps {
        sh 'sonar-scanner -Dsonar.projectBaseDir=$(pwd)'
      }
    }
  }

  post {
    always {
      echo 'POST: clean up our workspace'
      deleteDir()
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