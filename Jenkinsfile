pipeline {
    agent any

    stages {
        stage('Clone Juice Shop') {
            steps {
                git 'https://github.com/NguyenBDo/juice-shop'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("juice-shop")
                }
            }
        }
        stage('Run Juice Shop') {
            steps {
                script {
                    sh '''
                    docker rm -f juice-shop || true
                    docker run -d -p 3000:3000 --name juice-shop juice-shop
                    '''
                }
            }
        }
    }
}
