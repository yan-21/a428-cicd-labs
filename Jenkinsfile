node {
    stage('Build') {
        docker.image('node:16-buster-slim').inside("-p 3000:3000") {
	    checkout scm
            sh 'npm install'
        }
    }
    stage('Test') {
        docker.image('node:16-buster-slim').inside("-p 3000:3000") {
            sh './jenkins/scripts/test.sh'
        }
    }
    stage('Deploy') {
        docker.image('node:16-buster-slim').inside("-p 3000:3000") {
            sh './jenkins/scripts/deliver.sh'
	    input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)'
	    sh './jenkins/scripts/kill.sh'
        }
    }
}
