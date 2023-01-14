pipeline{
    agent any
    // environment {
    //     dockerImagename = "reddyashishaleti/myimage"
    //     appimage = ""
    // }
    stages{
        stage('Docker Build'){
            steps{
               
                sh "docker build -t reddyashishaleti/ashish:${env.BUILD_NUMBER} ."
            }
        }
        stage('Docker Push'){
            
            
            steps{
                script {
                   withCredentials([usernamePassword(credentialsId: 'Dockerhub', passwordVariable: 'passwordVariable', usernameVariable: 'usernameVariable')]){
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                    sh "docker push dockerImagename:${env.BUILD_NUMBER}"
                   }
                        
                    }
                }

            }
        
            stage('Remove Docker Image'){
                steps {
                    script {
                    sh 'docker version'
                    sh 'docker image list'
                    sh 'kubectl apply -f deployment.yml'
                }

            }

        }
    }
}
