pipeline{
    agent{
        label "slave"
    }
    tools{
        jdk 'java17'
        maven 'maven3'
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
    }














    
}