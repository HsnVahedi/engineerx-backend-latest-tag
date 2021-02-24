pipeline {
    agent any
    parameters {
        string(name: 'BACKEND_VERSION', defaultValue: 'latest')
    }
    stages {
        stage ('Update Image Tags') {
            steps {
                script {
                    withDockerRegistry([ credentialsId: "dockerhub-repo", url: "" ]) {
                        def backendImage = docker.image("hsndocker/backend:${params.BACKEND_VERSION}")
                        backendImage.push("latest")

                        def nginxImage = docker.image("hsndocker/backend-nginx:${params.BACKEND_VERSION}")
                        nginxImage.push("latest")

                        def postgresImage = docker.image("hsndocker/backend-postgres:${params.BACKEND_VERSION}")
                        postgresImage.push("latest")
                    }
                }
                
            }
        }
    }
}