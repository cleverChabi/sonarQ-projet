     pipeline {
        agent none
          
        tools {
          maven 'Maven'
        }

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
