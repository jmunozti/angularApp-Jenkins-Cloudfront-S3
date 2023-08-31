pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                nodejs(nodeJSInstallationName: 'nodeJS_16.20.1') {

                    echo 'Building..'
                    // Install Angular CLI globally
                    sh '/var/lib/jenkins/node/bin/npm install -g @angular/cli@12.2.14'
                    
                    // Install project dependencies
                    sh '    npm install'
                    
                    // Build your Angular project
                    sh 'ng build'
                }    
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