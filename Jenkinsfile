pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git credentialsId: 'github-access',
                    url: 'https://github.com/maximum-zero/web-count.git'
            }
        }

        stage('Build image') {
            steps {
                script {
                    dockerImage = docker.build("maximum0/web_count:v1.0")
                }
            }
        }

        stage('Push image') {
            steps {
                script {
                    withDockerRegistry([ credentialsId: "docker-access", url: "" ]) {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
