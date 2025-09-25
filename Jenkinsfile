pipeline {
    agent any

    tools {
        nodejs "NodeJs"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/keyurpatil06/DevOps-IA1.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Selenium IDE Tests') {
            steps {
                bat 'npm test'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs() // removes workspace files after build
        }
        success {
            echo 'Selenium IDE test pipeline completed successfully!'
        }
        failure {
            echo 'Selenium IDE test pipeline failed!'
        }
    }
}
