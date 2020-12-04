pipeline {
    agent any

    stages {
        stage('compile-code') {
            steps {
		sh './mvnw clean compile -e'		
            }
        }
	stage('test-code') {
            steps {
		sh './mvnw clean test -e'
            }
        }
	stage('jar-code') {
            steps {
		sh './mvnw clean package -e'
            }
        }
        stage('SonarQube analysis') {
	     steps {
    		   withSonarQubeEnv(installationName: 'sonar') { 
      		    // sh './mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
	            sh './mvn '
    		   }
	     }
	}
	stage('run-jar') {
            steps {
		sh 'nohup bash mvnw spring-boot:run &'
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
