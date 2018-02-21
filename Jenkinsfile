

def versionMajor = 0
def versionMinor = 14

pipeline {
  agent any

  stages {
    stage('Checkout'){
      steps {
        script {
          checkout scm
        }
      }
    }

    stage("Version"){
      steps{
        script{
          def commitHash = sh(returnStdout:true, script:'git rev-parse HEAD').trim()
          def revCount = sh(returnStdout: true, script: "git rev-list --no-merges --count $commitHash -- .").trim()
          env['VERSION'] = "v${versionMajor}.${versionMinor}.${revCount}-${GIT_BRANCH}"
          env['DOCKER_TAG'] = "finxact/core:${env.VERSION}"
        }
        echo env.VERSION
      }
    }
  }
}
