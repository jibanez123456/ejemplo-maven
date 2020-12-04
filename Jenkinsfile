pipeline {
    agent any

    stages {
        stage('compile-code') {
            steps {
                dir('C:\\Users\\jibanez\\DevOps\\Sesion5\\ejemplo-maven') {
					sh './mvnw clean compile -e'
				}
            }
        }
	stage('test-code') {
            steps {
                dir('C:\\Users\\jibanez\\DevOps\\Sesion5\\ejemplo-maven') {
					sh './mvnw clean test -e'
				}
            }
        }
	stage('jar-code') {
            steps {
                dir('C:\\Users\\jibanez\\DevOps\\Sesion5\\ejemplo-maven') {
					sh './mvnw clean package -e'
				}
            }
        }
        stage('SonarQube analysis') {
	     steps {
    		   withSonarQubeEnv(installationName: 'sonar') { 
      		    // sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
	            sh 'echo testing'
    		   }
	     }
	}
	stage('run-jar') {
            steps {
                dir('C:\\Users\\jibanez\\DevOps\\Sesion5\\ejemplo-maven') {
					sh 'nohup bash mvnw spring-boot:run &'
				}
            }
        }
        stage('esperando...') {
            steps {
                  sh 'sleep 10'
            }
        }
        stage('testing-aplication') {
            steps {
		  sh 'curl -X GET http://localhost:8081/rest/mscovid/test?msg=testing'
            }
        }

   }
}
