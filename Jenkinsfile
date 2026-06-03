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
    }
}
