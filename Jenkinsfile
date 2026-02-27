pipeline {
    agent any

    stages {

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t cicd-app .'
            }
        }

        stage('Docker Deploy') {
            steps {
                sh '''
                docker stop cicd-container || true
                docker rm cicd-container || true
                docker run -d -p 3000:3000 --name cicd-container cicd-app
                '''
            }
        }
    }
}
