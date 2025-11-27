pipeline {
    agent any

    stages {
        stage('Pull SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/lusiusevodius/springboot-app.git'
            }
        }
        
        stage('Containerized Apps') {
            steps {
                sh'''
                docker build -t 28011997/springboot-app:v3 .
                '''
            }
        }

        stage('Push to Registry') {
            steps {
                sh'''
                docker push 28011997/springboot-app:v3
                '''
            }
        }

        stage('Deploy Apps') {
            steps {
                sh'''
                kubectl apply -f manifest/
                '''
            }
        }   
    }
}