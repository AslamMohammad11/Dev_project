pipeline{
    agent{ label 'slave'}
    tools{
        jdk 'java17'
        maven 'maven3'
    }
    environment {
	    APP_NAME = "register-app-pipeline"
            RELEASE = "1.0.0"
            DOCKER_USER = "aslammohammad11"
            DOCKER_PASS = 'dockerhub-token'
            IMAGE_NAME = "${DOCKER_USER}" + "/" + "${APP_NAME}"
            IMAGE_TAG = "${RELEASE}-${BUILD_NUMBER}"
	        JENKINS_API_TOKEN = credentials("JENKINS_API_TOKEN")
    }
    stages{
        stage("Clean-workspace"){
            steps{
                cleanWs()
            }
        }

        stage("SCM-Checkout"){
            steps{
                git branch: 'main', credentialsId: 'git', url: 'https://github.com/AslamMohammad11/Dev_project.git'
            }
        }
        stage("BUild Application"){
            steps{
                sh 'mvn clean package'
            }
        }
        stage("Test Application"){
            steps{
                sh 'mvn test'
            }
        }

    }
}