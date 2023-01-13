pipeline{
    agent any
    environment {
        dockerImagename = "reddyashishaleti/dockerImagename"
        dockerImage = ""
    }
    stages{
        stage('Build Image'){
            steps{
                scripts{
                    dockerImage = docker.build dockerImage
                }
                
            }
        }
    }


}