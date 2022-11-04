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
                sh "echo push image 1"
            }
        }

        stage("Deploy"){
            steps {
                sh "echo deploy 1"
            }
        }
    }
}
