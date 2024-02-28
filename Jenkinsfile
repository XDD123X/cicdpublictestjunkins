pipeline {
    agent {
        node {
            label 'node1'
        }
    }
    environment {
        CC = 'clang'
    }
    stages {
        stage('Hello') {
            environment {
                name = 'Quan'
            }
            steps {
                sh 'printenv'
            }
        }
        stage('Build Image') {
            steps {
                script {
                    sh 'docker login -u quancgu -p quan123Cgu'
                    sh 'docker build -t quancgu/nginxcustom .'
                }
            }
        }
        stage('Push Image') {
            steps {
                script {
                    sh 'docker login -u quancgu -p quan123Cgu'
                    sh 'docker push quancgu/nginxcustom'
                }
            }
        }
    }
}