pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                script {
                    // Instala nvm
                    sh 'curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash'

                    // Fuente de nvm para que esté disponible en este shell
                    sh 'source ~/.nvm/nvm.sh'
                }
            }
        }
        stage('Install Node.js') {
            steps {
                script {
                    sh 'nvm install 16.20.1'
                    sh 'nvm use 16.20.1'
                }
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
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
                echo 'Testing..'
                 sh 'ng test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}