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
                sh 'echo Hello world!'
            }
        }
        stage('Build') {
            steps {
                script {
                    def dockerImage = docker.build('nginxcustom', '.')
                }
            }
        }
    }
}