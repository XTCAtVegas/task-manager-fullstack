pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                checkout scm
            }
        }
        
        stage('Build and Test') {
            steps {
                echo 'Building Docker images (this includes building frontend and backend)...'
                sh 'docker-compose build'
            }
        }
        
        stage('Verify Build') {
            steps {
                echo 'Verifying Docker images were created...'
                sh 'docker images | grep parent'
            }
        }
        
        stage('Push to Registry') {
            steps {
                echo 'Ready to push to Docker Hub!'
                echo 'Docker images built successfully ✅'
                echo '(Will configure Docker Hub push in next step)'
            }
        }
    }
    
    post {
        success {
            echo '=========================================='
            echo 'Pipeline completed successfully! ✅'
            echo 'Docker images are ready for deployment!'
            echo '=========================================='
        }
        failure {
            echo '=========================================='
            echo 'Pipeline failed! ❌'
            echo 'Check the logs above for errors'
            echo '=========================================='
        }
    }
}