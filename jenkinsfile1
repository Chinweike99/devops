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

	stage('Jenkins Environment') {
    	    steps {
        	sh 'echo "Job: $JOB_NAME"'
        	sh 'echo "Build number: $BUILD_NUMBER"'
        	sh 'echo "Build ID: $BUILD_ID"'
        	sh 'echo "Workspace: $WORKSPACE"'
        	sh 'echo "Node: $NODE_NAME"'
    	   }
	}
	
	stage('Environment Experiment') {
            steps {
                script {
                    echo "Jenkins build number: ${env.BUILD_NUMBER}"
                }

                sh '''
                    echo "Shell sees build number as:"
                    echo $BUILD_NUMBER
                '''
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
