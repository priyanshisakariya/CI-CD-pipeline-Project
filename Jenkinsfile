pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Build') {
            steps {
               bat 'mvn clean package -DskipTests'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t employee-management:v1 .'
            }
        }

        stage('Docker Run') {
            steps {
                bat 'docker stop emp-app'
                bat 'docker rm emp-app'
                bat 'docker run -d -p 8081:8081 --name emp-app employee-management:v1'
            }
        }
    }
}