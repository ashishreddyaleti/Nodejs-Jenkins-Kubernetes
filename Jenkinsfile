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
    stage("SSH Into k8s Server") {
        agent any
        def remote = [:]
        remote.name = 'K8S master'
        remote.host = '100.0.0.2'
        remote.user = 'vagrant'
        remote.password = 'vagrant'
        remote.allowAnyHosts = true

        stage('Put k8s-spring-boot-deployment.yml onto k8smaster') {
            sshPut remote: remote, from: '*.yml', into: '.'
        }

        stage('Deploy to minikube') {
          sshCommand remote: remote, command: "kubectl apply -f deployment.yml"
        }
    }


