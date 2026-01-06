node {
    stage('Clone repository') {
        git credentialsId: 'github-access', url: 'https://github.com/maximum-zero/web-count.git'
    }

    stage('Build image') {
       dockerImage = docker.build("maximum0/web_count:v1.0")
    }

    stage('Push image') {
        withDockerRegistry([ credentialsId: "docker-access", url: "" ]) {
        dockerImage.push()
        }
    }
}
