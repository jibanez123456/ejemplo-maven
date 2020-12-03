pipeline {
    agent any

    stages {
        stage('compile-code') {
            steps {
                dir('C:\\Users\\jibanez\\DevOps\\ejemplo-maven') {
					sh './mvnw clean compile -e'
				}
            }
        }
		stage('test-code') {
            steps {
                dir('C:\\Users\\jibanez\\DevOps\\ejemplo-maven') {
					sh './mvnw clean test -e'
				}
            }
        }
		stage('jar-code') {
            steps {
                dir('C:\\Users\\jibanez\\DevOps\\ejemplo-maven') {
					sh './mvnw clean package -e'
				}
            }
        }
		stage('run-jar') {
            steps {
                dir('C:\\Users\\jibanez\\DevOps\\ejemplo-maven') {
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