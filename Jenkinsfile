pipeline {
    agent any

    stages {
        stage('w/o docker') {
            steps {
                sh 'echo "Without docker"'
            }
        }

        stage('w/ docker') {
            // agent {
            //     dockerContainer {
            //         image 'node:18-alpine'
            //     }
            // }
            steps {
                sh 'echo "With docker"'
                sh 'npm --version'
            }
        }
    }
}
