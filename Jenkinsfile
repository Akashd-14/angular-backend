pipeline {
    agent any

    stages {
        stage('Pull') {
            steps {
                git branch: 'dev', url: 'https://github.com/Akashd-14/angular-backend.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Create Docker Image') {
            steps {
                sh '''
                docker build . -t akashdakave05/angular-backend:latest
                docker push akashdakave05/angular-backend:latest
                docker rmi akashdakave05/angular-backend:latest'''
            }
        }
        stage('Deployment') {
            steps {
                sh 'kubectl apply -f ./yaml/'
            }
        }
    }
}