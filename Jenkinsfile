pipeline {
    agent any
    environment {
        DOCKER_CREDENTIALS = credentials('dockerhublogin')
    }
    stages {
        stage('SCM Checkout') {
            steps {
                checkout scm
            }
        }
        // Uncomment and adjust the SonarQube stage as necessary.
        // Make sure you have the SonarScanner tool configured in Jenkins.
        /*
        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarScanner';
                    withSonarQubeEnv() {
                        bat "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
        */
        stage('Build Image') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'dockerhublogin', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        bat 'docker login -u %DOCKER_USERNAME% -p %DOCKER_PASSWORD%'
                    }
                    bat 'docker build -t nginxcustom .'
                }
            }
        }
        stage('Push Image') {
            steps {
                script {
                    bat 'docker tag nginxcustom:latest quancgu/nginxcustom:latest'
                    bat 'docker push quancgu/nginxcustom:latest'
                }
            }
        }
    }
}