pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub'
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing Python dependencies'

                sh '''
                    python3 -m venv venv
                    venv/bin/pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running Python unit tests'

                sh '''
                    venv/bin/python -m pytest tests/ -v
                '''
            }
        }

        stage('Build') {
            steps {
                echo 'Application build completed successfully'
            }
        }
    }

    post {
        success {
            echo 'Jenkins Multibranch Pipeline SUCCESS!'
        }

        failure {
            echo 'Jenkins Multibranch Pipeline FAILED!'
        }
    }
}