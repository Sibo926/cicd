pipeline {
    agent any

    tools {
        maven 'Maven 3.9.9'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Compiling Java project...'
                bat 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                bat 'mvn clean test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Packaging the application...'
                bat 'mvn package'
            }
        }

        stage('SonarQube analysis') {
            steps {
                echo 'Running SonarQube analysis...'
                withSonarQubeEnv('sonarqube-24.12.0.100206') {
                    bat 'mvn sonar:sonar -Dsonar.projectName="Project Java 1" -Dsonar.host.url=http://http://54.173.91.106:9000/'
                }
            }
        }
    }
}
