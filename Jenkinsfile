pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
		stage('Ejemplo shell script') {
            agent { label 'docker-agent' }
			steps {
                sh 'echo "Hello World 2"'
                sh '''
					hostname
                    echo "Multiline shell steps works too"
                    ls -lah
					pwd
                '''
            }
        }
		stage('Test') {
			when {
				branch "PR-*"
			}
            steps {
                sh "[[ 'Encantado de saludarte, Pedro' = \$echo 'Pedro'|./ejercicio.sh pruebas ]]";
				sh "[[ 'Encontraste el truco!: el primer parámetro del script es: sabeurp' = \$echo 'secreto'|./ejercicio.sh pruebas ]]";
            }
        }
    }
}