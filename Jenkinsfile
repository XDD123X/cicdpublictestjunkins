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
                sh 'ifconfig'
            }
        }
        stage('Build Image') {
            steps {
                script {
                    sh 'touch newfile.txt'
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