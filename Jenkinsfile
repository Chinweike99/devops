pipeline {
    agent {
        label 'nodejs'
    }

    parameters {
        choice(
            name: 'DEPLOY_ENV',
            choices: ['staging', 'production'],
            description: 'Environment for this build'
        )
    }

    environment {
        APP_NAME = 'jenkins-node-app'
    }

    stages {

        stage('Environment') {
            steps {
                echo "Application: ${env.APP_NAME}"
                echo "Deployment environment: ${params.DEPLOY_ENV}"
                echo "Build number: ${env.BUILD_NUMBER}"
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
                echo "Building ${env.APP_NAME}"
            }
        }
    }
}
