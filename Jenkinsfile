pipeline{
    agent any
    environment {
        dockerImagename = "reddyashishaleti/myimage"
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