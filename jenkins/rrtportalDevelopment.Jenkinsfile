pipeline {
    agent any

    stages {

        stage('Install Node.js') {
            steps {
                script {
                    // Define las versiones que deseas instalar
                    def nodeVersion = '16.20.1'
                    def npmVersion = '8.0.0'  // npm v7+ viene incluido con Node.js a partir de v16

                    // Descarga e instala Node.js
                    sh "curl -LO https://nodejs.org/dist/v${nodeVersion}/node-v${nodeVersion}-linux-x64.tar.xz"
                    sh "tar -xJf node-v${nodeVersion}-linux-x64.tar.xz"
                    sh "sudo cp -r node-v${nodeVersion}-linux-x64/* /usr/local/"

                    // Instala una versión específica de npm (opcional)
                    sh "sudo npm install -g npm@${npmVersion}"

                    // Limpia los archivos descargados
                    sh "rm -rf node-v${nodeVersion}-linux-x64*"
                    sh "ls && pwd"
                }
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                // Install Angular CLI globally
                sh '/var/lib/jenkins/node/bin/npm install -g @angular/cli@12.2.14'
                
                // Install project dependencies
                sh '    npm install'
                
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