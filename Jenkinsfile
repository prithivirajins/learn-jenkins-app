pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker {
                    image 'node:20-alpine'
                    reuseNode 'true'
                }
            }
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE')
                sh '''
                ls -la
                node --version
                npm --version
                npm ci || true
                npm run build
                ls -la
                '''
            }
        }
    }
}