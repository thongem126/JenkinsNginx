pipeline {
    agent any
    stages {
        stage("Build"){
            steps {
                sh "docker-compose build"
            }
        }

        stage("Push image"){
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                sh 'echo $DOCKER_PASSWORD | docker login --username $DOCKER_USERNAME --password-stdin'
                sh ""docker login -u="${DOCKER_USERNAME}" -p="${DOCKER_PASSWORD}"
                sh "docker push thongle0610/nginx:jenkins"

            }
        }

        stage("Deploy"){
            steps {
                sh "echo deploy 1"
            }
        }
    }
}
