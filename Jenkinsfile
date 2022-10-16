pipeline {
    agent {
        docker {
            image 'node:lts-buster-slim'
            args '-p 9090:9090'
        }
    }
    stages {
        stage('Npm Install') {
            steps {
                sh 'npm install'
            }
        }
	stage('Build Reactjs') {
            steps {
                sh 'npm run build'
            }
        }
    }
}
