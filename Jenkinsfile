pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t custom-nginx:1.0 .'
            }
        }

        stage('Run Container') {
            steps {
                echo 'Running Docker container...'
                sh '''
                    docker rm -f nginx-container || true
                    docker run -d --name nginx-container -p 8085:80 custom-nginx:1.0
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
        }
    }
}
