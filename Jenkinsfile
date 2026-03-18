pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {

        stage('Build') {
            steps {
                echo 'Feature branch update' 
                echo 'Building...'
                bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                bat 'mvn test'
            }
        }

        stage('Security Scan') {
    steps {
        echo 'Running Security Scan...'
        bat 'mvn org.owasp:dependency-check-maven:check'
    }
}

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                bat 'echo Deployment Done!'
            }
        }
    }
}
