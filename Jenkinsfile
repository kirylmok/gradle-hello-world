node ('slave1') {
  
  stage ('Checkout') {
    checkout scm
  }
  
  stage ('Build') {
    def gradleHome = tool 'gradle4'
    sh "${gradleHome}/bin/gradle build"
  }
  
  stage('post') {
    if ( currentBuild.result == 'SUCCESS') {
    addBadge(icon: 'success.gif', text: 'Success')
    }
    else if (currentBuild.result == 'FAILURE') {
    addBadge(icon: 'error.gif', text: 'Fail')
    } 
  }
