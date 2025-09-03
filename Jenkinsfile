pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/vinay-1729/task.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('my-static-site:latest')
                }
            }
        }

        stage('Stop Old Container') {
            steps {
                script {
                    sh '''
                        docker ps -q --filter "name=my-static-site" | grep -q . && docker stop my-static-site && docker rm my-static-site || true
                    '''
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker run -d --name my-static-site -p 8080:80 my-static-site:latest'
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."
        }
    }
}

