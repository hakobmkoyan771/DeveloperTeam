pipeline {
  agent any
  environment {
     
  }
  stages {
    stage("Compare TAG Before test & TAG after test") {
      steps {
         
      }
    }
  }
}
/*pipeline {
  agent any
  environment {
    BEFORE_TEST = ""
    AFTER_TEST = ""
  }
  stages {
    stage("Compare hash BEFORE_TEST & AFTER_TEST") {
      steps {
        script {
          AFTER_TEST = sh "git rev-parse hakobmkoyan771/PythonWorkdir --tags 1.0.0" 
          BEFORE_TEST = sh """docker exec redis_server redis-cli "get" "BEFORE_TEST" """
          echo BEFORE_TEST
          echo AFTER_TEST
          if(BEFORE_TEST != AFTER_TEST) 
          {
            error("Commit hash has been changed!") 
          }
        }
      }
    }
      stage('Release') {
         steps {
             step([$class: 'DockerComposeBuilder', dockerComposeFile: 'docker-compose.yml', option: [$class: 'StartService', scale: 1, service: 'server'], useCustomDockerComposeFile: true])  
         }
      }
   }
}
*/
