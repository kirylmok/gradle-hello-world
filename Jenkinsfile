node ('slave1') {
  currentBuild.currentResult = "Success"
  try {
    stage ('Checkout') {
      checkout scm
    }
  
    stage ('Build') {
      def gradleHome = tool 'gradle4'
      sh "${gradleHome}/bin/gradle build"
    }
  } catch (ex) {
    currentBuild.currentResult = "FAILURE"
    echo 'Error'
  }
  
  stage('post') {
    echo "Build status: " + currentBuild.currentResult
    if ( currentBuild.currentResult == 'SUCCESS') {
    addBadge(icon: 'success.gif', text: 'Success')
    }
    else if (currentBuild.currentResult == 'FAILURE') {
    addBadge(icon: 'error.gif', text: 'Fail')
    } 
  }
}
