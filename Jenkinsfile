pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    def dockerImage = docker.build("deeeye2/dobtest")
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Here you can add your test scripts
                    echo "Running tests..."
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials-id') {
                        def dockerImage = docker.build("deeeye2/dobtest")
                        dockerImage.push("latest")
                    }
                }
            }
        }
    }
}
