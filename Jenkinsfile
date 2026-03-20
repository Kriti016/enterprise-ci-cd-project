@Library('my-shared-lib') _

pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {

        stage('Build') {
            steps {
                echo 'Running Build from Shared Library...'
                buildApp()   // from shared library
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                bat 'mvn test'
            }
        }

        stage('API Test') {
            steps {
                echo 'Calling REST API...'
                bat 'curl -X GET https://jsonplaceholder.typicode.com/posts/1'
            }
        }

        stage('Environment Check') {
            steps {
                echo 'Checking system info...'
                bat 'echo Current Directory: %cd%'
                bat 'echo Java Version:'
                bat 'java -version'
                bat 'echo Maven Version:'
                bat 'mvn -version'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running Security Scan...'
                bat 'mvn org.owasp:dependency-check-maven:check -DfailBuildOnCVSS=7 -DskipUpdates=true'
            }
        }

        stage('Script Execution') {
            steps {
                echo 'Running script...'
                script {
                    try {
                        bat 'echo Script executed successfully'
                    } catch (Exception e) {
                        echo 'Error occurred in script execution'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                bat 'echo Deployment Done!'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check logs.'
        }
    }
}
