pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("my-app")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    docker.image("my-app").run("-p 8086:80")
                }
            }
        }
    }
}