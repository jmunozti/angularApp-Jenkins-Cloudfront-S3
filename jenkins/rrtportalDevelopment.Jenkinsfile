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

                    mv node-v${nodeVersion}-linux-x64 $PWD/node
                    export PATH=$PWD/node/bin:$PATH

                    ls /var/lib/jenkins/node/bin
                    """
                }
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                // Install Angular CLI globally
                sh '/var/lib/jenkins/node/bin/npm install -g @angular/cli@12.2.14'
                
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