pipeline {
    agent any  

    tools{
        maven 'Maven 3.9.9'
    }
    stages {    
        stage('Build') {
            steps {
                echo 'compiling java project...'
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                echo 'running unit tests...'
                sh 'mvn clean test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'packaging the application...'
                sh 'mvn package'
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
