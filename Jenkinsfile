@Library('my-pipeline-lib')
import libs.*
def base = new Base([ctx: this, orgName: 'ohralathe'])

pipeline {
  agent {
    node {
      label 'vg-host'
    }
    
  }
  stages {
    stage('Init') {
      steps {
        sh "echo `git config --get remote.origin.url`"
      }
    }

    stage('Pre-build') {
      steps {
        echo "Prebuild blabal dfd"
      }
    }

    stage('Build') {
      steps {
        parallel(
            "Build": {
              sh 'echo build'

            },
            "build win": {
              echo 'build for windows'
            },
            "build from shared lib": {
              script{
                base.build()
              }
            }
        )
      }

    }


    stage('Test') {
      steps {
        parallel(
          "Test": {
            sh 'echo check'
            
          },
          "Test on win": {
            echo 'test on windowd'
            
          }
        )
      }
    }

    stage('Deploy') {

      steps {
        sh 'echo Deploy'

        script {
          String message = "ablabalbal abla"
          echo message
        }
      }
    }
  }
  environment {
    ENV_VAR1 = '123'
  }
}