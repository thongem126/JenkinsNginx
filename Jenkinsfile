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
                sh "echo thong"
            }
        }

        stage("Deploy"){
            steps {
                sh "echo deploy 1"
            }
        }
    }
}
