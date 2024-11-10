pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    stages {
        stage('Compile') {
            steps {
                sh './mvnw clean compile' // Biên dịch mã Java
            }
        }
        
        stage('Scan') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    // Cấu hình đường dẫn cho sonar.java.binaries tới thư mục biên dịch
                    sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:3.9.0.2155:sonar -Dsonar.java.binaries=target/classes'
                }
            }
        }
    }
}
