pipeline{
    agent any
    stages{
        stage ('build'){
            steps{
                 echo 'build the image'
                 sh "docker build -t petclinic-app ."
            }
        }
        stage ('push to dockerhub'){
            steps{
                echo 'push code to dockerhub'
                withCredentials([usernamePassword(credentialsId:"dockerhubcred",passwordVariable:"dockerhubpass",usernameVariable:"dockerhubuser")]) {
                    sh "docker petclinic-app ${env.dockerhubuser}/petclinic-app:latest"
                    sh "docker login -u ${env.dockerhubuser} -p ${env.dockerhubpass}"
                    sh "docker push ${env.dockerhubuser}/petclinic-app:latest"
                }
            }
        }
    }
}
