node {
stage('push') {
withCredentials([usernamePassword(credentialsId: '64c4d161-f7f3-45e7-8562-71ea1b28b26d', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
    sh('git clone https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/pilipyukaaa/second.git')
}
}
//stage('Prepare/Checkout') { // for display purposes
//    dir('src') {
//       git branch: 'main', credentialsId:toket , url: 'https://github.com/pilipyukaaa/second.git'
//    }
//}
}
