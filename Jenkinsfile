pipeline {
    agent {
        label 'nodejs-agent'
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
                sh 'npm test -- --test-reporter=junit --test-reporter-destination=test-results.xml'
            }

            post {
                always {
                    junit(
                        testResults: 'test-results.xml',
                        allowEmptyResults: true
                    )
                }
            }
        }

        stage('Build') {
            steps {
                sh '''
                    mkdir -p dist
                    cp src/calculator.js dist/calculator.js
                    echo "Build number: $BUILD_NUMBER" > dist/build-info.txt
                '''
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts(
                    artifacts: 'dist/**',
                    fingerprint: true
                )
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t jenkins-learning-app:$BUILD_NUMBER .'
            }
        }
    }
}
