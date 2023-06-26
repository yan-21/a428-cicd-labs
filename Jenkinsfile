node {
    stage('Build and Test') {
        docker.image('node:16-buster-slim').inside("-p 3000:3000") {
            sh 'npm install'
            sh './jenkins/scripts/test.sh'
        }
    }
}