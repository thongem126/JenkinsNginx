pipeline {
    agent any
    stages {
        stage("Build"){
            steps {
                sh "docker build -t thongle0610/nginx:jenkins -f Dockerfile ."
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
