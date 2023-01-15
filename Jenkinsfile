pipeline{
    agent any
    environment {
        dockerImagename = "reddyashishaleti/myimage"
        appimage = ""
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
        }
        stage('Remove Docker Image'){
            steps {
                sh 'docker rmi reddyashishaleti/myimage${BUILD_NUMBER}'
                    

            }

        }
       
         }


    }


