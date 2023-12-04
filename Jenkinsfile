pipeline {
    agent {
        label 'linux'
    }
    tools {
        nodejs 'NodeJS'
        jdk 'JDK11'
        // git 'Default'
        maven 'Maven'
        // snyk 'Snyk'
        // dockerTool 'Docker'
    }
    // environment {
    //     // Define environment variables if needed
    //     NODEJS_HOME = tool 'NodeJS'
    //     PATH="${NODEJS_HOME}/bin:${PATH}"
    // }
    stages {
        // stage('Checkout') {
        //     steps {
        //         checkout scm
        //     }
        // }
        // stage('Install Dependencies') {
        //     steps {
        //         script {
        //             // Install npm dependencies
        //             sh 'npm install'
        //         }
        //     }
        // }
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
                    // Run tests if applicabl
                    // Add your test commands here
                    sh 'npm run test'
                }
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    // Execute SonarQube analysis
                    // Replace the placeholders with your SonarQube server details
                    sh "sonar-scanner \
                        -Dsonar.projectKey=angular-1 \
                        -Dsonar.sources=src \
                        -Dsonar.host.url=172.27.59.157:9000
                        -Dsonar.login=547eb616495ae5d6f0424a783bd18de965a93b15"
                }
            }
        }

        // stage('Deploy') {
        //     steps {
        //         // Add deployment steps here
        //         // For example, deploying to a web server or cloud platform
        //     }
        // }
    }
}
