

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
          def revCount = sh(returnStdout: true, script: "git rev-list --no-merges --count \$(git rev-parse HEAD) -- .").trim()
          env['VERSION'] = "v${versionMajor}.${versionMinor}.${revCount}-${GIT_BRANCH}"
          env['DOCKER_TAG'] = "finxact/core:${env.VERSION}"
        }
        echo env.VERSION
      }
    }
  }
}
