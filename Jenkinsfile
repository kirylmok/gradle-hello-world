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
    
      stage ('unit-test') {
        steps {
          sh "gradle test"
        }
      }
    
      stage ('func-test') {
        steps {
          tests = ["one" : { sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar otoMato 'Hello Otomato!'"},
                  "two" : { sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar kiRIll 'Hello Kirill!'"},
                  "three" : { sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar pLAYtIKA 'Hello Playtika!'"}]
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
