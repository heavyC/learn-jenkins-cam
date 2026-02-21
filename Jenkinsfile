pipeline {
    agent any

    stages {
        stage('Startup') {
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
        stage('Test') {
            steps {
                sh '''
                    echo "Testing"
                    test -f build/index.html
                    npm run test
                '''
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Deploying" (not doing anything yet)'
            }
        }
    }
}
