     pipeline {
        agent none
        stages {
         
          stage("build & sonarqube") {
            agent any
            steps {
              withSonarQubeEnv('SonarQube_Server') {
                sh 'mvn clean package sonar:sonar'
              }
            }
          }
        }
      }
