pipeline {
    agent any  // Jenkins puede ejecutar en cualquier nodo disponible

    stages {
        stage('Clonar Repositorio') {
            steps {
                git 'https://github.com/TU_USUARIO/SistemaGestion.git'
            }
        }

        stage('Compilar Proyecto') {
            steps {
                bat 'dotnet build SistemaGestion.sln --configuration Release'
            }
        }

        stage('Ejecutar Pruebas') {
            steps {
                bat 'dotnet test SistemaGestion.sln --logger trx --configuration Release'
            }
        }

        stage('Publicar Reportes') {
            steps {
                junit '**/TestResults/*.trx'  // Publica reportes de pruebas
            }
        }
    }
}
