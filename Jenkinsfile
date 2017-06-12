

//@Library('pipelib@master') _

node {
  stage("Setup") {
    git([
      url: "https://github.com/afroje-reshma/bftest-test",
      branch: "master"
    ])
  }

try {

  stage ("Health Check") {
              sh "pwd"
     def nodejs = tool 'NodeJS_6'
    def root = pwd()
    withEnv(["PATH+=${nodejs}/bin", "NPM_CONFIG_CACHE=${root}/.npmcache", "HOME=${WORKSPACE}"]) {
        sh "mkdir -p ${root}/.npmcache"
        sh "npm install newman"
        sh "ls -al"
        sh "ls -al node_modules/newman"   
              //sh "chmod u+x ci/Daily/daily.sh"
              //sh "ls -la ci/Daily"
              sh "npm install newman"
              sh "npm -v"
            //  sh "./ci/Daily/daily.sh"
      }
     }
    } 
        
        catch (err) {
      currentBuild.result = "FAILURE"
       mail body: "project build error is here: ${env.BUILD_URL}" ,
            subject: 'project build failed',
            to: 'afroje.reshma@gmail.com' 
       throw err
    }
 
  stage ("Cleanup") {
    deleteDir()
  }
 }

