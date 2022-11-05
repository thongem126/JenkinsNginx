pipeline {
    agent any
    environment {
        DOCKER_TAG = 'jenkins'
        DOCKER_IMAGE = "thongle0610/nginx"
    }
    
    stages {
        stage("Build"){
            steps {
                sh "docker build -t thongle0610/nginx:jenkins -f Dockerfile ."
            }
        }
        stage("Push image"){
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]){
                    sh 'echo $DOCKER_PASSWORD | docker login --username $DOCKER_USERNAME --password-stdin'
                }
                sh "docker push ${DOCKER_IMAGE}:${DOCKER_TAG}"
            }
        }
        stage("Deploy"){
            steps {
                sh "echo deploy 12"
            }
        }
    }
}

