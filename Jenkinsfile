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
        stage('Finish') {
            steps {
		sh "chmod +x -R ${env.WORKSPACE}"
                sh "cp -r ${env.WORKSPACE}/simple-node-js-react-npm-app/build/* /home/hik/dockApp/lamp/html/depo_kl_admin.dev/public_html/"
            }
        }
    }
}
