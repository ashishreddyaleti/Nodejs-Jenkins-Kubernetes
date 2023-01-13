pipeline{
    agent any
    environment {
        dockerImagename = "reddyashishaleti/myimage"
        dockerImage = ""
    }
    stages{
        stage('Build Image'){
            steps{
                script {
                    dockerImage = docker.build dockerImagename
                }
                
            }
        }
    }


}