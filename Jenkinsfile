pipeline {
    agent any

    tools {
        // Use the name of the Maven installation you've configured in Jenkins Global Tool Configuration
        maven 'mvn'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('my-SQserver-1') {
                    script {
                        // Since Maven is configured in 'tools', just use 'mvn'
                        sh 'mvn clean verify sonar:sonar'
                    }
                }
            }
        }

        stage('Build') {
            steps {
                // Again, just use 'mvn' as it's specified in 'tools'
                sh 'mvn clean package'
            }
        }
    }

    post {
        always {
            echo 'This will always run, lets check'
        }
        success {
            echo 'Build succeeded'
        }
        failure {
            echo 'Build failed'
        }
    }
}
