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

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f devops-demo || true

                docker run -d \
                  --name devops-demo \
                  -p 9095:80 \
                  devops-demo:v1
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'docker ps'
            }
        }
    }
}
