


pipeline {
    environment {
        LOGIN = "cparisfp"
        IMAGEN = "${LOGIN}/myapp"
        BUILD_NUMBER = "1"
        USUARIO = 'USER_DOCKERHUB'
    }

    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: "main", url: 'https://github.com/a25sarald/practica_7.1'
            }
        }
        stage('Build') {
            steps {
                script {
                    newApp = docker.build "$IMAGEN:$BUILD_NUMBER"
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    docker.withRegistry( '', USUARIO ) {
                        newApp.push()
                    }
                }
            }
        }
        stage('Clean Up') {
            steps {
                sh "docker rmi $IMAGEN:$BUILD_NUMBER"
                }
        }
    }
}











'''
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
'''