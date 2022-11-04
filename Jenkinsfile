pipeline {
    agent any
    stages {
        stage("Build"){
            steps {
                sh "sudo docker ps"
            }
        }

        stage("Push image"){
            steps {
                sh "echo thong1"
            }
        }

        stage("Deploy"){
            steps {
                sh "echo deploy 1"
            }
        }
    }
}
