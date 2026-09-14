pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Installing dependencies'
                sh 'echo npm install would run here'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
                sh 'echo npm test would run here'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan'
                sh 'echo security scanner would run here'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application'
                sh 'echo deployment would run here'
            }
        }
    }
}
