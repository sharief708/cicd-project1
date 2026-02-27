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
                docker rm -f cicd-container || true
                docker run -d -p 3000:3000 --name cicd-container cicd-app
                '''
            }
        }

    }
} 
