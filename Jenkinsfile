pipeline {
    agent any
    triggers {
        GenericTrigger(causeString: 'Generic Cause', 
                       genericVariables: [[key: 'chideminch', value: '$.repository.commits_url']])
    }
    stages {
        stage("print") {
            steps {
                echo "${chideminch}"
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
          AFTER_TEST = sh "git rev-parse refs/remotes/origin/main^{commit}" 
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
