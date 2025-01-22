     pipeline {
        agent none
          
        tools {
          maven 'Maven'
        }


        stages {

          stage("pre-commit & talisman") {
            agent any
            steps {
              echo 'Run the precomit'
            }
          }
             
          stage("build & sonarqube") {
            agent any
            steps {
              withSonarQubeEnv('SonarQube_Server') {
                sh 'mvn clean package sonar:sonar -e'
              }
            }
          }

           stage("deploy & OWASP Dependency-Check") {
            agent any
            steps {
               dependencyCheck additionalArguments: ''' 
                    -o './'
                    -s './'
                    -f 'ALL' 
                    --prettyPrint''', odcInstallation: 'owasp-dependency'
               dependencyCheckPublisher pattern: 'dependency-check-report.xml'
      }
          }
        }
      }
