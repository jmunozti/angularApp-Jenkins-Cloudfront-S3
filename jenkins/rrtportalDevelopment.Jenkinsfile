pipeline {
    agent any

    stages {

        stage('Install Node.js') {
            steps {
                script {
                    def nodeVersion = '16.20.1'
                    def nodeDownloadUrl = "https://nodejs.org/dist/v${nodeVersion}/node-v${nodeVersion}-linux-x64.tar.xz"
                    
                    sh """
                    curl -o node.tar.xz ${nodeDownloadUrl}
                    tar -xvf node.tar.xz
                    sudo mv node-v${nodeVersion}-linux-x64 /opt/node
                    export PATH=/opt/node/bin:$PATH
                    """
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