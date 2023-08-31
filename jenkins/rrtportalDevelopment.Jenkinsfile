pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from version control
            }
        }
        stage('Build') {
            steps {
                // Install Angular CLI globally
                sh 'npm install -g @angular/cli@12.2.14'
                
                // Install project dependencies
                sh 'npm install'
                
                // Build your Angular project
                sh 'ng build'
            }
        }
        stage('Test') {
            steps {
                // Run your tests
                sh 'ng test'
            }
        }
        stage('Deploy') {
            steps {
                // Deploy your Angular project
                // Add your deployment steps here
            }
        }
    }
}