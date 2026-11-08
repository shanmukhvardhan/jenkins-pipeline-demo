pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }
    post {
        success {
            mail to: 'YOUR_EMAIL@gmail.com',
                 subject: "SUCCESS: Pipeline ${currentBuild.fullDisplayName}",
                 body: "Good news! Your Jenkins pipeline build finished successfully."
        }
        failure {
            mail to: 'YOUR_EMAIL@gmail.com',
                 subject: "FAILURE: Pipeline ${currentBuild.fullDisplayName}",
                 body: "Your Jenkins pipeline build failed. Please check the Jenkins dashboard for logs."
        }
    }
}
