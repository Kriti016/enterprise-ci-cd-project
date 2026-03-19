@Library('my-shared-lib') _

pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {

        stage('Build') {
            steps {
                buildApp()
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
                bat 'mvn org.owasp:dependency-check-maven:check -DfailBuildOnCVSS=7 -DskipUpdates=true'
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
