
pipeline {
    agent {
        docker {
            image 'node:lts-slim'  // Usar unha imaxe oficial de Node.js
            //label 'docker'  // Etiqueta opcional para executar nun nodo con soporte Docker
            args '-u root'  // Opcional: Executar co usuario root si es necesario
        }
    }

    //environment {
        //NODE_HOME = '/usr/local/bin/node'  // Ruta á instalación de Node.js
        //PATH = "${NODE_HOME}/bin:${env.PATH}"  // Asegurarse de que Node.js estea no PATH
    //}

    stages {
          stage('Instalar Dependencias') {
            steps {
                script {
                    sh 'npm ci'
                }
            }
        }

        stage('Probas Unitarias') {
            steps {
                script {
                    sh 'npm test'
                }
            }
        }
       
    }
}
