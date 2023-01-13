*+pipeline {
  environment {
    dockerImageName = "reddyashishaleti/nodejs"
    dockerImage = ""
  }
     agent any 
     stages {
        // stage('checkout SCM') {
        //     steps {

        //         git credentialsId: 'github', url: 'https://github.com/ashishreddyaleti/Devops-React-Nodejs-Jenkins-Docker-kubernetes.git'
        //     }
            
        
        stage('BuildImage') {
            steps{
                script {
                    dockerImage = docker.build dockerImageName

                }
            }
        }
        stage('PushImage') {
            environment {
                dockerCredentials = 'Dockerhub'
            }
            steps{
                script {
                    def appimage = docker.build dockerImageName + "$BUILD_NUMBER"
                    docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub') {
                        appimage.push()
                        appimage.push('latest')
                    }

                }
            }
        }
        stage('Print yaml files'){
            steps{
                script {
                    sh 'cat deployment.yml'
                    sh 'cat deploymentservice.yml'
                }
            }
        }
        stage('Deploy to Kubernetes') {
            kubeconfig(credentialsId: 'kubernetes', serverUrl: '') {
            sh 'kubectl apply -f deployment.yml'
}
      

     }


}
}