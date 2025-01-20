pipeline {
    agent any
    environment {
        APP_ENV = "${Deploy}"
    }
    stages {
        stage('Build') {
            steps {
                echo "Installing dependencies in ${APP_ENV}"
                sh 'npm install || { echo "Build failed"; exit 1; }'
            }
        }
        stage('Test') {
            steps {
                echo "Running tests in ${APP_ENV}"
                sh 'npm run test || { echo "Tests failed"; exit 1; }'
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying Node.js app to ${APP_ENV} server"
                sh 'scp -o StrictHostKeyChecking=no server.js user@server:/var/www/${APP_ENV}/ || { echo "Deployment failed"; exit 1; }'
            }
        }
    }
}

