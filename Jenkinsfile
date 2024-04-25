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
    }

    post {
        success {
            echo 'Build and Deployment succeeded.'
        }
        failure {
            echo 'Build or Deployment failed.'
        }
    }
}
