pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Build stage'
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'Test step'
          }
        }

        stage('t1') {
          steps {
            echo 't-step1'
          }
        }

        stage('t3') {
          steps {
            echo 't-stage2'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'Prod-deploy'
        sleep 10
      }
    }

  }
}