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
        stage('PUSH IMAGE'){
            environment {
                dockerCredentilals = 'dockerCred'
            }
            steps{
                script {
                    def appimage = docker.build dockerImagename + "$BUILD_NUMBER"
                    docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub') {
                        appimage.push()
                        appimage.push('latest')
                        
                    }
                }

            }
            stage('Remove Docker Image'){
                steps {
                    script {
                    sh 'docker version'
                    sh 'docker rmi dockerImage'
                }

            }

        }
    }


}
}