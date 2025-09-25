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
                // Install Node.js if not available (Linux Jenkins agent)
                sh '''
                    if ! command -v node &> /dev/null
                    then
                        curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
                        sudo apt-get install -y nodejs
                    fi
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install selenium-side-runner + GeckoDriver (for Firefox)
                sh '''
                    npm install -g selenium-side-runner
                    wget https://github.com/mozilla/geckodriver/releases/latest/download/geckodriver-v0.35.0-linux64.tar.gz
                    tar -xvzf geckodriver-v0.35.0-linux64.tar.gz
                    sudo mv geckodriver /usr/local/bin/
                '''
            }
        }

        stage('Run Selenium IDE Test') {
            steps {
                sh 'selenium-side-runner Keyur_DEVOPS_IA.side'
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
