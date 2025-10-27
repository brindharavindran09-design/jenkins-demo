pipeline {
    agent any
    environment {        PYTHONPATH = "${env.WORKSPACE}"    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/brindharavindran09-design/jenkins-demo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh '. venv/bin/activate && pytest -v'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'python3 app.py'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
