
pipeline {
    agent any

    stages {
        stage('Check Environment') {
            steps {
                sh '''
                    node --version
                    npm --version
                    docker --version
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Build Application') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t furaha:v6 .'
            }
        }
    }

    post {
        success {
            echo 'Juice Shop pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the Jenkins console output.'
        }
    }
}
