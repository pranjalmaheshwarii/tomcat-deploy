pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'sudo docker build -t hello-world-app .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'sudo docker stop hello-world-app || true'
                sh 'sudo docker rm hello-world-app || true'
                sh 'sudo docker run -d --name hello-world-app -p 8091:8080 hello-world-app'
            }
        }
    }
}
