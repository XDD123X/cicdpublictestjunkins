pipeline {
    agent {
        node {
            label 'node2'
        }
    }
    environment {
        DOCKER_CREDENTIALS = credentials('dockerhublogin')
    }
    stages {
        // stage('Sonar Scan') {
        //     steps {
        //         script {
        //             withSonarQubeEnv(installations: 'sq1') {
        //                 sh ' sorna:sonar'
        //             }
        //         }
        //     }
        // }
        stage('Build Image') {
            steps {
                script {
                    sh "${DOCKER_PASSWORD}"
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
//change somthing