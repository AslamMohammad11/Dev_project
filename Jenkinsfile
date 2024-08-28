pipeline{
    agent{
        label "slave"
    }
    tools{
        jdk 'java17'
        maven 'maven3'
    }
    environment {
	        APP_NAME = "shopapp"
            RELEASE = "1.0.0"
            DOCKER_USER = "aslammohammad11"
            DOCKER_PASS = 'docker'
            IMAGE_NAME = "${DOCKER_USER}" + "/" + "${APP_NAME}"
            IMAGE_TAG = "${RELEASE}-${BUILD_NUMBER}"
	    
    }

    stages{
        stage("cleanup workspace"){
            steps{
                cleanWs()
            }

        }
        stage("SCM checkout"){
            steps{
                git branch: 'main', credentialsId: 'git', url: 'https://github.com/AslamMohammad11/Dev_project.git'
            }

        }
        stage("Build Application"){
            steps{
                sh "mvn clean package"
            }
        }
        stage("Test Application"){
            steps{
                sh "mvn test"
            }
        }
        stage("Build & Push Docker Image") {
            steps {
                script {
                    docker.withRegistry('',DOCKER_PASS) {
                        docker_image = docker.build "${IMAGE_NAME}"
                    }

                    docker.withRegistry('',DOCKER_PASS) {
                        docker_image.push("${IMAGE_TAG}")
                        docker_image.push('latest')
                    }
                }
            }
       }
    }   
}