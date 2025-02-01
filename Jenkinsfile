pipeline {
    agent any

    stages {
        stage('Clonar Repositorio') {
            steps {
                git branch: 'main', url: 'https://github.com/Jcbarahon/SistemaGestion.git'
            }
        }

        stage('Instalar Dependencias') {
            steps {
                bat 'dotnet restore SistemaGestion.sln'  // Asegurar que busca el archivo correcto
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
