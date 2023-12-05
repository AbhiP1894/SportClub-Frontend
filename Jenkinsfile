pipeline {
    agent {
        label 'linux'
    }
    // agent any
    
    tools {
        nodejs 'NodeJS'
        jdk 'JDK11'
        git 'Default'
        maven 'Maven'
        sonarscanner 'SonarScanner'
        //SonarScanner 'SonarScanner' type: 'hudson.plugins.sonar.SonarRunnerInstallation'
        // snyk 'Snyk'
        // dockerTool 'Docker'
    }

   
    // environment {
    //     // Define environment variables if needed
    //     NODEJS_HOME = tool 'NodeJS'
    //     PATH="${NODEJS_HOME}/bin:${PATH}"
    // }
    environment {
        // PATH="${tool 'SonarScanner '}/bin:${PATH}"
        SONAR_PROJECT_KEY = 'demo-app'
        SONAR_HOST_URL = 'http://172.27.59.157:9000'
    }

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
        // stage('Build') {
        //     steps {
        //         script {
        //             // Build Angular app
        //             sh 'npm run build -- --prod'
        //         }
        //     }
        // }
        // stage('Test') {
        //     steps {
        //         script {
        //             // Run tests if applicabl
        //             // Add your test commands here
        //             sh 'npm run test'
        //         }
        //     }
        // }
        stage('SonarQube Analysis') {
            // steps {
            //     script {
            //         // Execute SonarQube analysis
            //         // Replace the placeholders with your SonarQube server details
            //         bat 'npm run sonar'
            //     }credentialsId: 'sonar-token-1', installationName:
            // }
            when {
                branch 'snyk-demo'
            }
            steps {
                script {

                     withCredentials([string(credentialsId: 'sonar-token-1', variable: 'SONAR_TOKEN')]) {
                        // Run SonarQube scan
                        sh "sonar-scanner \
                            -Dsonar.projectKey=${SONAR_PROJECT_KEY} \
                            -Dsonar.host.url=${SONAR_HOST_URL} \
                            -Dsonar.login=${SONAR_TOKEN}"
                         
                    // // SonarQube Scanner stage
                    // withSonarQubeEnv('SonarScanner') {
                    //     sh "sonar-scanner \
                    //         -Dsonar.projectKey=demo-app \
                    //         -Dsonar.sources=src \
                    //         -Dsonar.host.url=http://172.27.59.157:9000 \
                    //         -Dsonar.login=sonar-token-1"
                    // }
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
