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
       			 // Use the wrapper! It already has the permissions we need.
       			 sh './gradlew jar'
        
       			 // Then archive the resulting jar file
        		 archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
    			}
		}
    	}
}
