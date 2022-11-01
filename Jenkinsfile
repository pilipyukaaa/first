pipeline {
  agent any

  stages {
    stage('clone') {
      steps {
        dir('src') {
        withCredentials([usernamePassword(credentialsId: '64c4d161-f7f3-45e7-8562-71ea1b28b26d', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
          sh('rm -rf src*')
          sh('git clone https://${GIT_USERNAME}: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@github.com/pilipyukaaa/second.git')
        }
      }
    }
    }
    stage('Build') {
      steps {
        sh "echo BUILD_NUMBER=${env.BUILD_NUMBER}"
        sh 'sed -i "s/myimage:0.0.*/myimage:$BUILD_NUMBER/g" second/version.yml'
      }
    }
    stage('push') {
      steps {
        withCredentials([usernamePassword(credentialsId: '64c4d161-f7f3-45e7-8562-71ea1b28b26d', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
          sh("cd second; git config --global user.email 'pilipyukaa@gmail.com'")
          sh("cd second; git config --global user.name '$GIT_USERNAME'")
          sh("cd second; git add version.yml")
          sh("cd second; git commit -m 'changed version to $BUILD_NUMBER by jenkins'")
          sh('cd second; git push https://${GIT_USERNAME}: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@github.com/pilipyukaaa/second.git --tags')
        }
      }
    }
  }
}
