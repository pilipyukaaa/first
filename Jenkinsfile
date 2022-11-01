node {
stage('push') {
withCredentials([usernamePassword(credentialsId: '64c4d161-f7f3-45e7-8562-71ea1b28b26d', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
    sh('git clone https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/pilipyukaaa/second.git')
}
}
stage('Build') {

  if (isUnix()) {
     sh "echo BUILD_NUMBER=${env.BUILD_NUMBER}"
     sh "sed -i 's+\\(image: myrepo\\.com/myimage:0.0.\\)[.0-9]*+\\1$BUILD_NUMBER+' src/version.yml "
  } else {
     sh "echo BUILD_NUMBER=${env.BUILD_NUMBER}"
  }
}
}
stage('push') {
withCredentials([usernamePassword(credentialsId: '64c4d161-f7f3-45e7-8562-71ea1b28b26d', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
    sh("git tag -a some_tag -m 'Jenkins'")
    sh('git push https://${GIT_USERNAME}:${GIT_PASSWORD}@https://github.com/pilipyukaaa/second.git --tags')
}
}
