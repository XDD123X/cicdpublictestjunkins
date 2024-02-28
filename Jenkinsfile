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
                sh 'whoami'
            }
        }
        stage('Build Image') {
            steps {
                script {
                    sh 'docker build -t nginxcustom .'
                }
            }
        }
        // stage('Push Image') {
        //     steps {
        //         script {
        //             sh 'docker push quancgu/nginxcustom'
        //         }
        //     }
        // }
    }
}