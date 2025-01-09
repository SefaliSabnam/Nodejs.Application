pipeline {
    agent any
    environment {
        APP_ENV = "${BRANCH_NAME}"
    }
    stages {
        stage('Build') {
            steps {
                echo "Installing dependencies in ${APP_ENV}"
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo "Running tests in ${APP_ENV}"
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying Node.js app to ${APP_ENV} server"
                sh 'scp server.js user@server:/var/www/${APP_ENV}/'
            }
        }
    }
}

