pipeline{
    agent{ label 'slave'}
    tools{
        jdk 'java17'
        maven 'maven3'
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
        stage("Build & Push Docker Image") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub-token'){
                      sh "docker build -t aslammohammad11/dev-pro-img:tag1221 ."
                      sh "docker push aslammohammad11/dev-pro-img:tag1221" 
                    }
                    
                   }
                }
         }
   }

}