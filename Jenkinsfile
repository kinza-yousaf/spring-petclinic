pipeline {
    agent any

    environment {
        // Define environment variables if necessary
    }

    stages {
        stage('Checkout') {
            steps {
                // Check out the code from the GitHub repository
                git url: 'https://github.com/kinza-yousaf/spring-petclinic.git'
            }
        }

        stage('SonarQube analysis') {
            steps {
                // Run SonarQube analysis
                withSonarQubeEnv('my-SQserver-1') {
                    script {
                        // If your project uses Maven:
                        sh 'mvn clean verify sonar:sonar'
                        
                        // If your project uses Gradle:
                        // sh './gradlew sonarqube'
                    }
                }
            }
        }

        stage('Build') {
            steps {
                // Build the project, e.g., with Maven
                sh 'mvn clean package'
            }
        }
    }

    post {
        // Define post-build actions
        always {
            // e.g., clean up, notify someone, etc.
        }
        success {
            // Actions to perform if the build was successful
        }
        failure {
            // Actions to perform if the build failed
        }
    }
}
