pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'echo "Without docker"'
            }
        }

        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    alwaysPull false
                    reuseNode true  // ← ADD THIS - Critical!
                }
            }
            steps {
                sh '''
                    echo "With docker"
                    ls -la
                    node --version
                    npm --version
                    npm ci 
                    npm run build
                    ls -la
                '''

            }
        }
    }
}
