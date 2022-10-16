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
        stage('Test') {
            steps {
		sh 'chmod +x -R ${env.WORKSPACE}'
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') { 
            steps {
		sh 'chmod +x -R ${env.WORKSPACE}'
                sh './jenkins/scripts/deliver.sh' 
                input message: 'Finished using the web site? (Click "Proceed" to continue)' 
                sh './jenkins/scripts/kill.sh' 
            }
        }
    }
}
