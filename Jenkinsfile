pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Source Code Ready'
            }
        }

        stage('Docker Version') {
            steps {
                sh 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-demo:v1 .'
            }
        }

        stage('List Images') {
            steps {
                sh 'docker images'
            }
        }
    }
}
