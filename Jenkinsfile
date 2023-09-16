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
    }
}
