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

        stage('Deploy') {
            steps {
                // Running the Ansible playbook
                sh 'ansible-playbook -i /path/to/inventory/file deploy_petclinic.yaml'
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
