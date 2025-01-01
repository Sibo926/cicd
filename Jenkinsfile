pipeline {
    agent any

    tools {
        maven 'Maven 3.9.9'
    }

    environment {
        SONAR_TOKEN = credentials('SonarToken')  // Replace with your Jenkins credentials ID for SonarQube token
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
                withSonarQubeEnv('SonarScanner') {
                    bat '''
                        mvn clean verify sonar:sonar \
                          -Dsonar.projectKey=Project-Java-1 \
                          -Dsonar.projectName="Project Java 1" \
                          -Dsonar.host.url=http://54.173.91.106:9000 \
                          -Dsonar.token=sqp_e7f4ae69d15691dc8a1bc82e5d493bb3e9562628
                    '''
                }
            }
        }
    }
}
