pipeline {
    agent any

    stages {
        stage('Clone the source code') {
            steps {
                git branch: 'main', url: 'https://github.com/mayurwaghmode/docker-demo.git'
            }
        }
        stage('Build the code') {
            steps {
                sh 'python3 app.py'
            }
        }
        
        stage('Create a docker image') {
            steps {
                sh 'docker build -f Dockerfile -t mwaghmodepersistent/calci:addition .'
            }
        }
        
        stage('docker login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', passwordVariable: 'password', usernameVariable: 'username')]) {
                    sh 'docker login -u $username -p $password'
            }
            }
        }
        
        stage('push the image') {
            steps {
                sh 'docker push mwaghmodepersistent/calci:addition'
            }
        }
    }
}
