pipeline {
	agent any

	environment {
		IMAGE_NAME = "apache-jenkins:${env.BUILD_NUMBER}"
	}

	stages {
		stage('Checkout') {
			steps {
				checkout scm
			}
		}

		stage('Build Docker Image') {
			steps {
				script {
                    echo "Building docker image"
					docker.build(IMAGE_NAME, "-f dockerfile .")
				}
			}
		}

		stage('Archive Web Content') {
			steps {
				archiveArtifacts artifacts: 'web/**', fingerprint: true
			}
		}
	}
}
