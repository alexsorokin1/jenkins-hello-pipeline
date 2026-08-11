pipeline {
    agent {
        docker {
            image 'python:3.12-slim'
            args '-v jenkins-pip-cache:/root/.cache/pip'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                sh 'ls -la'
            }
        }

        stage('Lint') {
            steps {
                sh 'pip install ruff'
                sh 'ruff check .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Pretend deploy step — this is where CD will go later'
                sh 'python app.py'
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished ✔'
        }
        failure {
            echo 'Pipeline failed ✘'
        }
    }
}
