node {   
stages {
        stage('Prepare src code') { 
            dir('src') {
                git branch: 'master',
                    credentialsId: 'toket',
                    url: 'https://github.com/pilipyukaaa/second.git'
                
                sh "ls -lat"
            }
        }
}
