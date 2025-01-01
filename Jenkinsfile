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
            stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        withSonarQubeEnv('sonarqube-6.2.1.4610') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
        sh "mvn sonar:sonar"
    }
        }
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
