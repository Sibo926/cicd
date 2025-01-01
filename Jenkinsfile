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
   node {
  stage('SCM') {
    git 'https://github.com/Sibo926/cicd'
  }
  stage('SonarQube analysis') {
    // withSonarQubeEnv(credentialsId: 'f225455e-ea59-40fa-8af7-08176e86507a', installationName: 'My SonarQube Server') { // You can override the credential to be used
      sh 'mvn sonar:sonar'
    }
  }
}
