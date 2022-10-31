node {   
def gradleHome

stage('Prepare/Checkout') { // for display purposes
    dir('src') {
       git branch: 'main', url: 'https://github.com/pilipyukaaa/second.git'
    }
}

stage('Build') {
  // Run the gradle build
  if (isUnix()) {
     sh "echo hello"
  } else {
     sh "echo "BUILD_NUMBER=${env.BUILD_NUMBER}"
  }
}
}

print "Hello World!\n"
