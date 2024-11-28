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
                 script {
                    def result = sh(script: 'npm ci', returnStatus: true)
                    if (result != 0) {
                        echo "npm ci failed, but continuing pipeline"
                    }
                }
                sh '''
                ls -la
                node --version
                npm --version
                npm cache clean --force
                npm ci || true
                npm run build
                ls -la
                '''
            }
        }
    }
}