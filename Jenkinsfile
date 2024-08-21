pipeline{
    agent{ any }
    stages{
        stage("SCM-Checkout"){
            steps{
                git branch: 'main', credentialsId: 'git', url: 'https://github.com/AslamMohammad11/Dev_project.git'
            }
            }
        }
    }