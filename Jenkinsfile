

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
              sh "./ci/Daily/Daily_BF_Depend.sh"
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

