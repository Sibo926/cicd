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
        
        // SonarQube analysis stage
        stage('SonarQube analysis') {
            steps {
                echo 'Running SonarQube analysis...'
                withSonarQubeEnv('My SonarQube Server') {
                    bat 'mvn sonar:sonar'
                }
            }
        }
        
        // SCM Checkout (could be redundant since 'Checkout' already happens earlier)
        stage('SCM') {
            steps {
                git 'https://github.com/Sibo926/cicd'
            }
        }
    }
}
