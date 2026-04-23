pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                git branch: '2026Q1',
                url: 'https://github.com/pratiksha-awsdevops5/docker-app.git'
            }
        }

        stage ('Build image') {
            steps {
                sh 'docker build -t httpd:latest /var/lib/jenkins/workspace/docker-assign-1'
            }
        }

        stage('Deploy container'){
            steps{
                sh """
                    docker stop c1 || true
                    docker rm c1 || true
                    docker run -d --name c1 -p 80:80 httpd:latest
                """
            }
        }
    }
}
