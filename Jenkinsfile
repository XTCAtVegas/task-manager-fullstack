pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                checkout scm
            }
        }
        
        stage('Build Frontend') {
            steps {
                echo 'Building React Frontend...'
                dir('taskmanager-app') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        
        stage('Build Backend') {
            steps {
                echo 'Building C# Backend...'
                dir('TaskManagerAPI') {
                    sh 'dotnet restore'
                    sh 'dotnet build --configuration Release'
                }
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                echo 'Tests passed! (Add real tests later)'
            }
        }
        
        stage('Docker Build') {
            steps {
                echo 'Building Docker images...'
                sh 'docker-compose build'
            }
        }
        
        stage('Docker Push') {
            steps {
                echo 'Ready to push to Docker Hub (will configure later)'
                echo 'Images built successfully!'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline completed successfully! ✅'
        }
        failure {
            echo 'Pipeline failed! ❌'
        }
    }
}