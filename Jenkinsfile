pipeline {
    agent any

    stages {
        stage('w/o docker') {
            steps {
                sh 'echo "Without docker"'
            }
        }

        stage('w/ docker') {
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
