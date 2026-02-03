pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                // Use the absolute path to gradle
                sh '/home/cloud/gradle-8.5/bin/gradle clean test'
            }
        }

        stage('Archive Artifact') {
            steps {
                sh '/home/cloud/gradle-8.5/bin/gradle jar'
                archiveArtifacts artifacts: 'build/libs/*.jar', allowEmptyArchive: false
            }
        }
    }
}
