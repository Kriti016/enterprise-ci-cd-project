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

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                bat 'echo Deployment Done!'
            }
        }
    }
}
