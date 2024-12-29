     pipeline {
        agent none
        stages {
         
          stage("build & sonarqube") {
            agent any
            steps {
              withSonarQubeEnv('sonarqube server') {
                bat 'mvn clean package sonar:sonar'
              }
            }
          }
        }
      }
