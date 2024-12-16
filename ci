pipeline {
    agent any
    stages {
        stage('Preparar Entorno') {
            steps {
                script {
                    echo 'Preparando el entorno...'
                    sh 'php --version' // Verifica que PHP esté instalado
                }
            }
        }
        stage('Instalar Dependencias') {
            steps {
                script {
                    echo 'Instalando dependencias...'
                    sh 'composer install' // Instala las dependencias
                }
            }
        }
        stage('Ejecutar Pruebas Unitarias') {
            steps {
                script {
                    echo 'Ejecutando pruebas unitarias...'
                    sh './vendor/bin/phpunit' // Ejecuta PHPUnit
                }
            }
        }
        stage('Análisis de Calidad de Código') {
            steps {
                script {
                    echo 'Analizando calidad de código...'
                    sh './vendor/bin/phpcs --standard=PSR12 src/' // Analiza la calidad del código
                }
            }
        }
    }
    post {
        always {
            script {
                echo 'Limpieza finalizada.'
            }
        }
        success {
            script {
                echo 'Integración Continua completada exitosamente.'
            }
        }
        failure {
            script {
                echo 'La CI falló. Revisar logs.'
            }
        }
    }
}
