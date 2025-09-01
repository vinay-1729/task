pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/<your-username>/<repo-name>.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('my-static-site:latest')
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    docker.image('my-static-site:latest').run('-d -p 8080:80')
                }
            }
        }
    }
}

