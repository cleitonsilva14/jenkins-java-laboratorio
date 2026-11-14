
pipeline {
    agent any

    stages {

        stage('Compilacao') {
            steps {
                echo 'Iniciando compilacao Java...'

                sh '''
                    mkdir -p build
                    javac -d build src/App.java
                '''

                echo 'Compilacao concluida!'
            }
        }

        stage('Publicar Artefatos') {
            steps {
                echo 'Publicando arquivos compilados...'

                archiveArtifacts artifacts: 'build/*.class',
                                fingerprint: true
            }
        }

        stage('Execucao') {
            steps {
                echo 'Executando aplicacao Java...'

                sh 'java -cp build App'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executado com sucesso!'
        }

        failure {
            echo 'Ocorreu um erro no Pipeline!'
        }
    }
}
