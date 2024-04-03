pipeline {
    agent any

    tools {
        // mvn is the name of the Maven installation I've configured in Jenkins Global Tool Configuration
        maven 'mvn'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Using maven to build
                sh 'mvn clean package'
            }
        }

        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('my-SQserver-1') {
                    script {
                        // Performing static analysis
                        sh 'mvn clean verify sonar:sonar'
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Build succeeded.'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
