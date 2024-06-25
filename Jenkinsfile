pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/tu_usuario/tu_repositorio.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('mi-nginx-imagen')
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Detenemos y eliminamos cualquier contenedor en ejecución con el mismo nombre
                    sh 'docker rm -f mi-nginx-contenedor || true'
                    // Lanzamos el contenedor con el nombre 'mi-nginx-contenedor' en el puerto 8080
                    docker.run('-d -p 8080:80 --name mi-nginx-contenedor mi-nginx-imagen')
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline terminado.'
        }
    }
}
