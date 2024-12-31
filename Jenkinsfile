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
                echo 'compiling java project...'
                bat 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                echo 'running unit tests...'
                bat 'mvn clean test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'packaging the application...'
                bat 'mvn package'
            }
        }
    }

    post {   
        always {
            echo 'pipeline run finished.'
        }
        success {
            echo 'pipeline was successful.'
        }
        failure {
            echo 'pipeline failed.'
        }
    }
}
