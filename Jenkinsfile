pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Build') {
            steps { sh 'chmod +x gradlew'
                sh './gradlew build' }
        }
        stage('Test') {
            steps { sh './gradlew test' }
        }
        stage('Package') {
            steps {
                sh './gradlew jar'
                archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
            }
        }
    }
    post {
        success { echo "Pipeline completed successfully!" }
        failure { echo "Pipeline failed." }
    }
}
