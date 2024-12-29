pipeline {
    agent any
      environment {
        SONARQUBE_URL = 'http://localhost:9000' // Replace with your SonarQube server URL
        SONARQUBE_TOKEN = 'sqp_1bdeed67e9c23e0d748a8db46579386c5c778a88' // Replace with your SonarQube token
        SONARQUBE_PROJECT_KEY = 'mavenn' // Replace with your SonarQube project key
        SONARQUBE_PROJECT_NAME = 'mavenn' // Replace with your SonarQube project name
    }
    stages {
        stage("Build & SonarQube Analysis") {
            agent {
                label 'any' // Can be changed based on the specific Jenkins agent label
            }
            steps {
                script {
                    withSonarQubeEnv('sonarqube server') {
                        echo "Starting Maven build and SonarQube analysis..."
                        bat 'mvn clean verify sonar:sonar'
                    }
                }
            }
        }
    }
    post {
        always {
            echo "Pipeline execution completed."
        }
        success {
            echo "Build and SonarQube analysis succeeded!"
        }
        failure {
            echo "Pipeline failed! Please check the logs for errors."
        }
    }
}
