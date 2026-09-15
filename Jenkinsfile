pipeline {
    agent {
        label 'nodejs'
    }

    stages {

        stage('Environment') {
            steps {
                sh 'node --version'
                sh 'npm --version'
                sh 'java --version'
                sh 'git --version'
                sh 'whoami'
                sh 'pwd'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application'
            }
        }
    }
}
