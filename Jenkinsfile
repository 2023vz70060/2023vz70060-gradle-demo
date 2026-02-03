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
        		// Ensure the wrapper is executable within the workspace
        		sh 'chmod +x gradlew'
        		// Run using the wrapper
       			 sh './gradlew clean test'
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
