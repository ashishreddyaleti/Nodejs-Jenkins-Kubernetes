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
        stage('SSH intto Remote') {
         
            def remote = [:]
            remote.name = 'minikubeHost'
            remote.host = 'localhost'
            remote.user = 'aaleti'
            remote.password = 'Aryareddy@27'
            remote.allowAnyHost = true
        
         }
        stage('copy files to remote'){
            
            sshPut remote: remote, from: '*yml', into: '.'
        }
         }


    }


