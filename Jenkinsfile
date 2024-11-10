pipeline {
    agent any
    tools {
        maven 'maven'
    }
    
    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/DevOps-Video-Sharing/UserService-NT548.git' // Use your Git repository URL
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn compile'
            }
        }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        
        stage('SonarQube Analysis') {
            environment {
                SONAR_HOST_URL = 'http://103.9.157.149:9000' // Replace with your SonarQube URL
                SONAR_AUTH_TOKEN = credentials('sonarqube') // Store your token in Jenkins credentials
            }
            steps {
                sh 'mvn sonar:sonar -Dsonar.projectKey=sample_project -Dsonar.host.url=$SONAR_HOST_URL -Dsonar.login=$SONAR_AUTH_TOKEN'
            }
        }       
    }
}