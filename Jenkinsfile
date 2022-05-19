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
          echo "abc"
          dir('DevRepo') {
            git branch: 'main', url: "${REPO_LINK}" 
            COMMIT_SHA_AFTER_TEST = sh returnStdout: true, script: "git rev-list -n 1 ${TAG_NAME}"
            echo COMMIT_SHA_AFTER_TEST
            echo COMMIT_SHA
            if("${COMMIT_SHA_AFTER_TEST}" == "${COMMIT_SHA}") {
              error("Commit hashes are not equal each other") 
            }
          }
        }
      }
    }
  }
}
