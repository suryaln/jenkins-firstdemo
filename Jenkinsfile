pipeline {
    agent any
    environment {
        dockerhub = "suryaln/sam"
        DOCKER = 'cred'
    }
    stages {
        stage('Cloning') {
            steps {
                git branch: 'main', url: 'https://github.com/suryaln/jenkins-firstdemo.git'
            }
        }
        stage('build Image') {
            steps {
                sh '''docker build -t imaging .
                docker tag imaging $dockerhub'''
            }
        }
        stage('pushing image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'cred', passwordVariable: 'pass', usernameVariable: 'user')]) {
                sh "echo \$DOCKER_PASSWORD | docker login -u \$DOCKER_USERNAME --password-stdin docker.io"
                }              
            }
        }
    }
}
