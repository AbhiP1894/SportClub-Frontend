pipeline {
    agent any

    environment {
        // Define environment variables if needed
        NODEJS_HOME = tool 'NodeJS'
        PATH="${NODEJS_HOME}/bin:${PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install npm dependencies
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build Angular app
                    sh 'npm run build -- --prod'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run tests if applicable
                    // Add your test commands here
                    sh 'npm run test'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Add deployment steps here
                // For example, deploying to a web server or cloud platform
            }
        }
    }

    post {
        always {
            // Clean up steps, if needed
        }
    }
}
