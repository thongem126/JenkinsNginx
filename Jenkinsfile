pipeline {
    agent any
    environment {
        DOCKER_TAG = 'jenkins'
        DOCKER_IMAGE = 'thongle0610/nginx'
        ANSIBLE_HOST = '/var/lib/jenkins/workspace/testjenkins'


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
                tools {ansible "ansible"}
                dir("$ANSIBLE_HOST"){
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]){
                        ansiblePlaybook(
                            credentialsId: 'ubuntu',
                            playbook: 'playbook.yml',
                            inventory: 'hosts.ini',
                            become: 'yes',
                        extraVars: [
                            DOCKER_USERNAME: "${DOCKER_USERNAME}", 
                            DOCKER_PASSWORD: "${DOCKER_PASSWORD}" 
                            ]
                        )
                    }
                }
            }
        }
    }
}

