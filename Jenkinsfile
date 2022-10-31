#!/usr/bin/env groovy
import hudson.model.*
node {   
    
stage('Prepare/Checkout') { // for display purposes
    dir('src') {
       git branch: 'main', url: 'https://github.com/pilipyukaaa/second.git'
    }
}

stage('Build') {
  // Run the gradle build
  if (isUnix()) {
     sh "echo BUILD_NUMBER=${env.BUILD_NUMBER}"
     sh "sed -i 's+\\(image: myrepo\\.com/myimage:0.0.\\)[.0-9]*+\\1$BUILD_NUMBER+' src/version.yml "
  } else {
     sh "echo BUILD_NUMBER=${env.BUILD_NUMBER}"
  }
}
}
withCredentials([string(credentialsId: 'GIT_PASSWORD', variable: 'TEXT')]) {
    sh('echo $GIT_PASSWORD')

}
