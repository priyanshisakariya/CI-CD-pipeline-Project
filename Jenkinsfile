pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/priyanshisakariya/CI-CD-pipeline-Project.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t employee-management:v1 .'
            }
        }

        stage('Docker Run') {
            steps {
                bat 'docker stop emp-app || exit 0'
                bat 'docker rm emp-app || exit 0'
                bat 'docker run -d -p 8081:8081 --name emp-app employee-management:v1'
            }
        }
    }
}