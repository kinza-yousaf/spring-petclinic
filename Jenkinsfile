pipeline {
    agent any

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
    always {
        echo 'This will always run'
    }
    success {
        echo 'Build succeeded'
    }
    failure {
        echo 'Build failed'
    }
}

}
