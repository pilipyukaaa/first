pipeline {
  agent any

  stages {
    stage('clone') {
      steps {
        dir('src') {
        withCredentials([usernamePassword(credentialsId: '64c4d161-f7f3-45e7-8562-71ea1b28b26d', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
          sh('rm -rf  ./*')
          sh('pwd')
          sh('git clone https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/pilipyukaaa/second.git')
        }
      }
    }
    }

    stage('push') {
      steps {
        withCredentials([usernamePassword(credentialsId: '64c4d161-f7f3-45e7-8562-71ea1b28b26d', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
          sh("cd src/second; git config --global user.email 'pilipyukaa@gmail.com'")
          sh("cd src/second; git config --global user.name '$GIT_USERNAME'")
          sh("cd src/second; git checkout change_version")
          sh "echo BUILD_NUMBER=${env.BUILD_NUMBER}"
          sh 'sed -i -r "s/myimage:.+/myimage:$BUILD_NUMBER/g" src/second/version.yml'
          sh 'cat src/second/version.yml'
          sh("cd src/second; git add version.yml")
          sh("cd src/second; git commit -m 'changed version to $BUILD_NUMBER by jenkins'")
          sh('cd src/second; git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/pilipyukaaa/second.git')
        }
      }
    }
  }
}
