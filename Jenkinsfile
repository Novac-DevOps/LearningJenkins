// Jenkinsfile
pipeline {
    agent any

    environment {
        IMAGE_NAME = 'novac28/learningjenkins'
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/Novac-DevOps/LearningJenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'sudo docker build -t $IMAGE_NAME .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'sudo docker run -d -p 5000:5000 --name flask_app $IMAGE_NAME'
                }
            }
        }

        stage('Clean up') {
            steps {
                script {
                    sh 'sudo docker rm -f flask_app || true'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished'
        }
    }
}
