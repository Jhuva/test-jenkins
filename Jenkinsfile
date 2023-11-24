pipeline {
    agent any
    
    environment {
        // Definir variables de entorno si es necesario
        MAVEN_HOME = tool 'maven'
    }

    stages {
        stage('Checkout') {
            steps {
                // Clonar el repositorio de GitHub
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Compilar el proyecto con Maven
                script {
                    sh "${MAVEN_HOME}/bin/mvn clean install"
                }
            }
        }

        stage('Deploy to Dev') {
            when {
                branch 'develop'
            }
            steps {
                // Desplegar en el entorno de desarrollo
                // Puedes agregar comandos o scripts específicos para el despliegue
                script {
                    sh 'echo ESTE VA CONFIGURACIONES DE DESARROLLO'
                    sh 'echo Desarrollo'
                }
            }
        }

        stage('Deploy to QA') {
            when {
                branch 'qa'
            }
            steps {
                // Desplegar en el entorno de QA
                script {
                    sh "echo ESTE VA A AMBIENTE DE PRUEBAS"
                    sh "echo QA"
                }
            }
        }

        stage('Deploy to Production') {
            when {
                branch 'main'
            }
            steps {
                // Desplegar en el entorno de producción
                script {
                    sh "echo ESTE VA A AMBIENTE DE PRODUCCIÓN"
                    sh "echo PRODUCCIÓN"
                }
            }
        }
    }
}