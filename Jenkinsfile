pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Beeshan-Gowda/Automated-Deployment-Pipeline.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('my-app:latest')
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    docker.image('my-app:latest').inside {
                        sh 'npm test'
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    docker.image('my-app:latest').run('-d -p 3000:3000')
                }
            }
        }
    }
}

