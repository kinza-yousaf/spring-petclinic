pipeline {
    agent any

    stages {
        steps {
        checkout scm
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
