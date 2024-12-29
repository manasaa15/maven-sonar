pipeline {
    agent none
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
