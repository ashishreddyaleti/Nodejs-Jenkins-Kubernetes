pipeline{
    agent any
    environment {
        dockerImagename = "reddyashishaleti/myimage"
        appimage = ""
    }
    stages{
        // stage('Build Image'){
        //     steps{
        //         script {
        //             dockerImage = docker.build dockerImagename
        //         }
                
        //     }
        // }
        // stage('PUSH IMAGE'){
        //     environment {
        //         dockerCredentilals = 'dockerCred'
        //     }
        //     steps{
        //         script {
        //             def appimage = docker.build dockerImagename + "$BUILD_NUMBER"
        //             docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub') {
        //                 appimage.push()
        //                 appimage.push('latest')
                        
        //             }
        //         }

        //     }
        // }
        // stage('Remove Docker Image'){
        //     steps {
        //         sh 'docker rmi reddyashishaleti/myimage${BUILD_NUMBER}'
                    

        //     }

        // }
        stage('Deploy to minikube') {

            steps{
                sh 'ip a'
                sh 'cp /home/aaleti/.kube/config /home/jenkins/.kube/'
                // withKubeConfig([credentialsId: 'kubernetes']){
                //     sh 'cat deployment.yml | sed "s/{{BUILD_NUMBER}}/$BUILD_NUMBER/g" | kubectl apply -f -'
                //     sh 'kubectl apply -f service.yml'
                // }
            }
        }

    }


}
