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
           sh "gradle clean build"
        }
      }
    
      stage ('unit-test') {
        steps {
          sh "gradle test"
          junit "build/test-results/junit-platform/*.xml"
        }
      }
    
      stage('func-test'){
        steps{
            parallel(
                "First test" : {
                    sh "sh test-data/int-test.sh build/libs/oto-gradle-1.0.jar tOMAto 'Hello Tomato!'"
                },
                "Second test" : {
                    sh "sh test-data/int-test.sh build/libs/oto-gradle-1.0.jar kiRILL 'Hello Kirill!'"
                },
                "third step" : {
                    sh "sh test-data/int-test.sh build/libs/oto-gradle-1.0.jar pLayTIKA 'Hello Playtika!'"
                }
            )
        }
    }
    }

    post {
      success {
          addBadge(icon: 'success.gif', text: 'Success')
      }
      
      failure {
          addBadge(icon: 'red.gif', text: 'Fail')
      }
    }
}
