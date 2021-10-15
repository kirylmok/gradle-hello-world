pipeline {
  agent {
    label 'slave1'
  }
  tools {
    gradle 'gradle4'
  }
  stages {
      stage ('Checkout') {
        steps {
          checkout scm
        }
      }
      stage ('Build') {
        steps {
          sh "${gradleHome}/bin/gradle build"
        }
      }
  }

    post {
      success {
        script {
          echo "Build status: " + currentBuild.result
          if ( currentBuild.result == 'SUCCESS') {
          addBadge(icon: 'success.gif', text: 'Success')
          }
        }
      }
      failure {
        script {
          if (currentBuild.result == 'FAILURE') {
          addBadge(icon: 'error.gif', text: 'Fail')
          }
        }
      }
  }
}
