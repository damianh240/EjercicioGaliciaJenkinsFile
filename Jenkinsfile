pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/damianh240/EjercicioGalicia.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('mi-imagen:latest')
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    docker.image('mi-imagen:latest').run('-p 8000:8000')
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
