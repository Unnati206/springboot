pipeline {

    agent any

    stages {

        stage('Git Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Unnati206/Springboot16.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t springbootapp .'
            }
        }

        stage('Docker Deploy') {
            steps {
                sh '''
                docker stop springbootapp || true
                docker rm springbootapp || true

                docker run -d \
                --name springbootapp \
                -p 8080:8080 \
                springbootapp
                '''
            }
        }
    }
}