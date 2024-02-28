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
            step([$class: 'DockerBuilderPublisher', cleanImages: true, cleanupWithJenkinsJobDelete: true, cloud: '', dockerFileDirectory: '', fromRegistry: [], pushCredentialsId: '', pushOnSuccess: true, tagsString: 'nginxcustom'])
        }
    }
}