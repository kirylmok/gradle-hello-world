node ('slave1') {
  currentBuild.result = "Success"
  try {
    stage ('Checkout') {
      checkout scm
    }
    stage ('Build') {
      def gradleHome = tool 'gradle4'
      sh "${gradleHome}/bin/gradle build"
    }
  } catch (ex) {
    currentBuild.result = "FAILURE"
    echo 'Error'
  }
  
  stage('post') {
    echo "Build status: " + currentBuild.result
    if ( currentBuild.result == 'SUCCESS') {
    addBadge(icon: 'success.gif', text: 'Success')
    }
    else if (currentBuild.result == 'FAILURE') {
    addBadge(icon: 'error.gif', text: 'Fail')
    } 
  }
}
