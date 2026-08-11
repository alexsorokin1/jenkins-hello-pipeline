pipeline {
	stage('Lint') {
            steps {
                sh 'pip install --user ruff'
                sh '/tmp/.local/bin/ruff check .'
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
