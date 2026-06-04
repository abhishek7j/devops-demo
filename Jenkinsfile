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

        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {

                    sh '''
                    echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin

                    docker tag devops-demo:v1 abhishek7j/devops-demo:v1

                    docker push abhishek7j/devops-demo:v1
                    '''
                }
            }
        }
    }
}
