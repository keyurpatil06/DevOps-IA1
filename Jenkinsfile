pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/keyurpatil06/DevOps-IA1.git'
            }
        }

        stage('Setup Node.js') {
            steps {
                bat '''
                node -v
                if %ERRORLEVEL% NEQ 0 (
                    echo Node.js is not installed. Please install Node.js manually on Jenkins server.
                    exit 1
                )
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '''
                npm install -g selenium-side-runner
                curl -LO https://github.com/mozilla/geckodriver/releases/latest/download/geckodriver-v0.35.0-win64.zip
                tar -xf geckodriver-v0.35.0-win64.zip
                move geckodriver.exe C:\\Windows\\System32\\
                '''
            }
        }

        stage('Run Selenium IDE Test') {
            steps {
                bat 'selenium-side-runner Keyur_DEVOPS_IA.side'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
        }
        success {
            echo 'Selenium IDE test pipeline completed successfully!'
        }
        failure {
            echo 'Selenium IDE test pipeline failed!'
        }
    }
}