pipeline {
    agent {
        node {
            label 'node2'
        }
    }
    environment {
        DOCKER_CREDENTIALS = credentials('dockerhublogin') // Thay 'dockerhublogin' bằng ID của Credential bạn đã tạo trong Jenkins
    }
    stages {
        stage('Build Image') {
            steps {
                script {
                    // Thực hiện đăng nhập Docker
                    withCredentials([usernamePassword(credentialsId: 'dockerhublogin', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}"
                    }
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
