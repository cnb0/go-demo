pipeline {
    agent any
	environment {
		SOURCE_PATH='/root/jenkins/jenkins/workspace/demo-go'
		SONAR_URL='http://134.209.106.104:9000'
		SONAR_SECRET='4f2dcaf29fb346a115bf22586b31b67615e0f080'
	}
    stages {
		stage('Pull code') {
            steps {
				git branch: "main",
				url: 'https://github.com/up1/demo-go-sonarqube.git'
            }
        }
        stage('Build') {
            steps {
                sh 'make clean && make build'
            }
        }
		stage('Testing') {
            steps {
                sh 'make test'
            }
        }
		stage('SonarQube analysis') {
            steps {
                sh 'make start-sonar-scanner'
            }
        }
    }
}