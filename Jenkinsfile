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
                sh "${MAVEN_HOME}/bin/mvn clean install"
            }
        }

        stage('Deploy to Dev') {
            when {
                branch 'develop'
            }
            steps {
                // Desplegar en el entorno de desarrollo
                // Puedes agregar comandos o scripts específicos para el despliegue
                echo "ESTE VA CONFIGURACIONES DE DESARROLLO"
                echo "Desarrollo"
            }
        }

        stage('Deploy to QA') {
            when {
                branch 'qa'
            }
            steps {
                // Desplegar en el entorno de QA
                echo "ESTE VA A AMBIENTE DE PRUEBAS"
                echo "QA"
            }
        }

        stage('Deploy to Production') {
            when {
                branch 'main'
            }
            steps {
                // Desplegar en el entorno de producción
                echo "ESTE VA A AMBIENTE DE PRODUCCIÓN"
                echo "PRODUCCIÓN"
            }
        }
    }
}