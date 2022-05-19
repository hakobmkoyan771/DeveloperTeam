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
[?1049h[22;0;0t[>4;2m[?1h=[?2004h[?1004h[1;43r[?12h[?12l[22;2t[22;1t[27m[23m[29m[m[H[2J[?25l[43;1H"echo" [New][2;1H[94m~                                                                                                                                                                               [3;1H~                                                                                                                                                                               [4;1H~                                                                                                                                                                               [5;1H~                                                                                                                                                                               [6;1H~                                                                                                                                                                               [7;1H~                                                                                                                                                                               [8;1H~                                                                                                                                                                               [9;1H~                                                                                                                                                                               [10;1H~                                                                                                                                                                               [11;1H~                                                                                                                                                                               [12;1H~                                                                                                                                                                               [13;1H~                                                                                                                                                                               [14;1H~                                                                                                                                                                               [15;1H~                                                                                                                                                                               [16;1H~                                                                                                                                                                               [17;1H~                                                                                                                                                                               [18;1H~                                                                                                                                                                               [19;1H~                                                                                                                                                                               [20;1H~                                                                                                                                                                               [21;1H~                                                                                                                                                                               [22;1H~                                                                                                                                                                               [23;1H~                                                                                                                                                                               [24;1H~                                                                                                                                                                               [25;1H~                                                                                                                                                                               [26;1H~                                                                                                                                                                               [27;1H~                                                                                                                                                                               [28;1H~                                                                                                                                                                               [29;1H~                                                                                                                                                                               [30;1H~                                                                                                                                                                               [31;1H~                                                                                                                                                                               [32;1H~                                                                                                                                                                               [33;1H~                                                                                                                                                                               [34;1H~                                                                                                                                                                               [35;1H~                                                                                                                                                                               [36;1H~                                                                                                                                                                               [37;1H~                                                                                                                                                                               [38;1H~                                                                                                                                                                               [39;1H~                                                                                                                                                                               [40;1H~                                                                                                                                                                               [41;1H~                                                                                                                                                                               [42;1H~                                                                                                                                                                               [m[43;159H0,0-1[9CAll[1;1H[?25h[?25l[43;1HType  :qa  and press <Enter> to exit Vim[43;159H[K[43;159H0,0-1[9CAll[1;1H[?25h[?25l[43;159H[K[43;159H0,0-1[9CAll[1;1H[?25h[?25l[43;159H[K[43;159H0,0-1[9CAll[1;1H[?25h[?25l[43;159H[K[43;159H0,0-1[9CAll[1;1H[?25h[?25l[43;159H[K[43;159H0,0-1[9CAll[1;1H[?25h[?25l[43;159H[K[43;159H0,0-1[9CAll[1;1H[?25h[?25l[43;159H[K[43;159H0,0-1[9CAll[1;1H[?25h[?25l[43;159H[K[43;159H0,0-1[9CAll[1;1H[?25h[?25l[43;159H[K[43;159H0,0-1[9CAll[1;1H[?25h[?25l[43;149H^D[1;1H[43;149H  [1;1H[?25h[43;1H[?2004l[>4;m[?1004l[?2004l[?1l>[>4;m[?1049l[23;0;0tVim: Error reading input, exiting...
Vim: Finished.
[43;1H[?25h[23;2t[23;1t[J2 files to edit
a
