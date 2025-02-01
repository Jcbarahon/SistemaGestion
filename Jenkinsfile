pipeline {
    agent any

    stages {
        stage('Clonar Repositorio') {
            steps {
                // Asegúrate de que se esté clonando la rama main
                git branch: 'main', url: 'https://github.com/Jcbarahon/SistemaGestion.git'
            }
        }

        stage('Instalar Dependencias') {
            steps {
                bat 'dotnet restore'
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

        stage('Publicar Reportes de Pruebas') {
            steps {
                junit '**/TestResults/*.trx'
            }
        }
    }
}
