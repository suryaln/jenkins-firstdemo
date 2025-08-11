pipeline {
    agent any
    environment {
        dockerhub = "suryaln/sam"
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
                sh 'docker login -u $Docker_User -p $Docker_password'
                sh 'docker push $dockerhub'              
            }
        }
    }
}
