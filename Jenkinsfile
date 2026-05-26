pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {  
                echo 'Cloning repository...'
                git branch: 'main',
                credentialsId: 'github-creds',
                url: 'https://github.com/pravinchoudhari-01/Cloud-Native-DevSecOps-Platform-App.git'
            }
        }

        stage('Verify Server') {
            steps {
                sh 'whoami'
                sh 'docker --version'
                sh 'kubectl version --client'
            }
        }

        stage('Build Frontend Docker Image') {
            steps {
                sh 'docker build -t frontend-test ./app/frontend'
            }
        }

    }
}
