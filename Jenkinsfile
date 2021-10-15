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
    
      stage ('call gradle'){
        steps {
           sh "gradle build" 
        }
      }
    }

    post {
      success {
          addBadge(icon: 'success.gif', text: 'Success')
      }
      
      failure {
          addBadge(icon: 'error.gif', text: 'Fail')
      }
    }
}
