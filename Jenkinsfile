pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/your-username/your-repo.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-web-app .'
            }
        }
        
        stage('Run Container') {
            steps {
                sh 'docker stop my-web-app-container || true'
                sh 'docker rm my-web-app-container || true'
                sh 'docker run -d -p 8080:80 --name my-web-app-container my-web-app'
            }
        }
    }
}
