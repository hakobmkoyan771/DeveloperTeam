pipeline {
  agent any
  environment {
     COMMIT_SHA_AFTER_TEST = ""
     TAG_NAME = ""
     COMMIT_SHA = ""
     REPO_LINK = ""
  }
  stages {
    stage("Initialize Variables") {
      steps {
        script {
          TAG_NAME = sh returnStdout: true, script: """docker exec redis_server redis-cli 'get' 'TAG_NAME' """
          COMMIT_SHA = sh returnStdout: true, script: """docker exec redis_server redis-cli 'get' 'COMMIT_HASH' """
          REPO_LINK = sh returnStdout: true, script: """docker exec redis_server redis-cli 'get' 'DEV_REPO' """      
        }
      }
    }
    stage("Compare TAG Before test & TAG after test") {
      steps {
        script {
          dir('DevRepo') {
            git branch: 'main', url: "${REPO_LINK}" 
            COMMIT_SHA_AFTER_TEST = sh returnStdout: true, script: "git rev-list -n 1 ${TAG_NAME}"
            echo COMMIT_SHA_AFTER_TEST
            echo COMMIT_SHA
            if("${COMMIT_SHA_AFTER_TEST}" != "${COMMIT_SHA}") {
              error("Commit hashes are not equal each other") 
            }
          }
         /* COMMIT_SHA_AFTER_TEST = sh """git ls-remote rev-list -n 1 ${RELEASE_TAG}"""
          if(COMMIT_SHA_AFTER_TEST != RELEASE_TAG) {
             error("Commit hash has been changed!")
          }*/
        }
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
