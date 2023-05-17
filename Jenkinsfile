pipeline {
    agent any


    stages {
        stage("Git Checkout"){
            steps{
                git 'https://github.com/Ojong90/jenkins-repo.git'
            }
        }
        
        stage('Build Docker image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'DOCKER_HUB_TOKEN') {
                        def imageName = 'nkpotojong/wonderful'
                        def imageTag = 'latest'
                        
                        sh "docker build -t ${imageName}:${imageTag} ."
                    }
                }
            }
        }
        
        stage('Push Docker image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'DOCKER_HUB_TOKEN') {
                        def imageName = 'nkpotojong/wonderful'
                        def imageTag = 'latest'
                        
                        sh "docker push ${imageName}:${imageTag}"
                    }
                }
            }
        }
    }
}
