pipeline {
  agent {
    label 'slave1'
  }
  stages {
      stage ('Checkout') {
        steps {
          checkout scm
        }
      }
      stage ('Build') {
        steps {
          def gradleHome = tool 'gradle4'
          sh "${gradleHome}/bin/gradle build"
        }
      }
    }

    post {
      success {
        echo "Build status: " + currentBuild.result
        if ( currentBuild.result == 'SUCCESS') {
        addBadge(icon: 'success.gif', text: 'Success')
        }
      }
      failure {
        if (currentBuild.result == 'FAILURE') {
        addBadge(icon: 'error.gif', text: 'Fail')
        } 
      }
  }
}
