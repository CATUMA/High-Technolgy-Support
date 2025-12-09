pipeline {
    // Define que el pipeline se puede ejecutar en cualquier agente disponible
    agent any 

    // Define las credenciales de Git que se usarán (las que creaste como 'github-creds')
    environment {
        // Asegúrate de que 'github-creds' sea el ID que usaste en Jenkins
        GITHUB_CREDS = 'github-creds' 
    }

    stages {
        stage('Checkout') {
            steps {
                echo '>> 1. Obteniendo codigo desde GitHub...'
                // Usa las credenciales almacenadas en Jenkins para clonar tu repositorio
                git branch: 'main', credentialsId: env.GITHUB_CREDS, url: 'https://github.com/CATUMA/High-Technolgy-Support.git'
            }
        }
        
        stage('Build') {
            steps {
                echo '>> 2. Compilando aplicacion...'
                // Si tu proyecto es un HTML simple, solo se simula
                // Si fuera Java/Maven o Node.js, aquí iría el comando de compilación (ej: sh 'mvn clean install' o sh 'npm install')
                sh 'echo "Simulacion de compilacion exitosa."' 
            }
        }
        
        stage('Test') {
            steps {
                echo '>> 3. Ejecutando pruebas unitarias...'
                // En un entorno real, aquí iría el comando de pruebas (ej: sh 'npm test' o sh 'mvn test')
                sh 'echo "Simulacion de pruebas exitosa."' 
            }
        }
        
        stage('Package Release') {
            steps {
                echo '>> 4. Generando artefacto release...'
                // Este paso simula el empaquetado del release mencionado en tu documento
                // Se crea un archivo zip llamado release.zip con el contenido del workspace
                sh 'zip -r release.zip ./*' 
                sh 'echo "Artefacto release.zip generado exitosamente."'
            }
        }
        
        stage('Publish Artifact') {
            steps {
                echo '>> 5. Publicando el artefacto y limpiando...'
                // Este paso archiva el release.zip en Jenkins para que pueda ser descargado
                archiveArtifacts artifacts: 'release.zip', fingerprint: true
                sh 'echo "Artefacto publicado en Jenkins."'
            }
        }
    }
}