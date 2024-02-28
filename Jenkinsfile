pipeline {
    agent {
        node {
            label 'node2'
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
                sh 'whoami'
                sh 'ifconfig'
            }
        }
        stage('Build Image') {
            steps {
                script {
                    sh 'docker build -t nginxcustom .'
                }
            }
        }
        stage('Push Image') {
            steps {
                script {
                    sh 'docker tag nginxcustom:latest quancgu/nginxcustom:latest'
                    sh 'docker push quancgu/nginxcustom'
                }
            }
        }
    }
}