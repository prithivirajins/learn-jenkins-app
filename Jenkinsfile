pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker {
                    image 'node:20-alpine'
                    reuseNode 'true'
                    args '-u root'
                }
            }
            steps {
                 
                sh '''
                ls -la
                node --version
                npm --version
                npm cache clean --force
                npm ci 
                npm run build
                ls -la
                '''
            }
        }
    }
}