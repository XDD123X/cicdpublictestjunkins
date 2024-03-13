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
        
        stage('SonarQube analysis') {
            def scannerHome = tool 'SonarScanner 4.0';
            withSonarQubeEnv('My SonarQube Server') { 
            sh "${scannerHome}/bin/sonar-scanner"
            }
        }
        
        stage('Build Image') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'dockerhublogin', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh 'docker login -u %DOCKER_USERNAME% -p %DOCKER_PASSWORD%'
                    }
                    sh 'docker build -t nginxcustom .'
                }
            }
        }
        stage('Push Image') {
            steps {
                script {
                    sh 'docker tag nginxcustom:latest quancgu/nginxcustom:latest'
                    sh 'docker push quancgu/nginxcustom:latest'
                }
            }
        }
    }
}